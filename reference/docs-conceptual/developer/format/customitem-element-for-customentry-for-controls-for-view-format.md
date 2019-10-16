---
title: Élément CustomItem pour CustomEntry pour les contrôles pour View (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33cb5350-73ef-4b79-a879-0edf051869e4
caps.latest.revision: 7
ms.openlocfilehash: 174ba6a14819f823ec39f72e49a626e781221d8c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363938"
---
# <a name="customitem-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="aaad0-102">CustomItem, élément pour CustomEntry pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="aaad0-102">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="aaad0-103">Définit les données affichées par le contrôle et leur mode d’affichage.</span><span class="sxs-lookup"><span data-stu-id="aaad0-103">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="aaad0-104">Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.</span><span class="sxs-lookup"><span data-stu-id="aaad0-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="aaad0-105">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) contrôle l’élément (format) Control, élément pour les contrôles pour View (format) CustomControl, élément de Control pour les contrôles pour l’élément View (format) CustomEntries pour CustomControl pour View (format) CustomEntry, élément pour CustomEntries pour les contrôles pour l’élément CustomItem (format) View pour CustomEntry pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="aaad0-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="aaad0-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aaad0-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...<Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="aaad0-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="aaad0-107">Attributes and Elements</span></span>

<span data-ttu-id="aaad0-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `CustomItem`.</span><span class="sxs-lookup"><span data-stu-id="aaad0-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="aaad0-109">Pour plus d’informations, consultez la section Notes.</span><span class="sxs-lookup"><span data-stu-id="aaad0-109">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="aaad0-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="aaad0-110">Attributes</span></span>

<span data-ttu-id="aaad0-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="aaad0-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="aaad0-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="aaad0-112">Child Elements</span></span>

|<span data-ttu-id="aaad0-113">Élément</span><span class="sxs-lookup"><span data-stu-id="aaad0-113">Element</span></span>|<span data-ttu-id="aaad0-114">Description</span><span class="sxs-lookup"><span data-stu-id="aaad0-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="aaad0-115">Élément ExpressionBinding pour CustomItem pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="aaad0-115">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="aaad0-116">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="aaad0-116">Optional element.</span></span><br /><br /> <span data-ttu-id="aaad0-117">Définit les données affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="aaad0-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="aaad0-118">Élément Frame pour CustomItem pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="aaad0-118">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="aaad0-119">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="aaad0-119">Optional element.</span></span><br /><br /> <span data-ttu-id="aaad0-120">Définit le mode d’affichage des données, par exemple en décalant les données à gauche ou à droite.</span><span class="sxs-lookup"><span data-stu-id="aaad0-120">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="aaad0-121">Élément NewLine pour CustomItem pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="aaad0-121">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="aaad0-122">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="aaad0-122">Optional element.</span></span><br /><br /> <span data-ttu-id="aaad0-123">Ajoute une ligne vide à l’affichage du contrôle.</span><span class="sxs-lookup"><span data-stu-id="aaad0-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="aaad0-124">Élément Text pour CustomItem pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="aaad0-124">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="aaad0-125">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="aaad0-125">Optional element.</span></span><br /><br /> <span data-ttu-id="aaad0-126">Ajoute du texte, tel que des parenthèses ou des crochets, à l’affichage du contrôle.</span><span class="sxs-lookup"><span data-stu-id="aaad0-126">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="aaad0-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="aaad0-127">Parent Elements</span></span>

|<span data-ttu-id="aaad0-128">Élément</span><span class="sxs-lookup"><span data-stu-id="aaad0-128">Element</span></span>|<span data-ttu-id="aaad0-129">Description</span><span class="sxs-lookup"><span data-stu-id="aaad0-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="aaad0-130">Élément CustomEntry pour CustomEntries pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="aaad0-130">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="aaad0-131">Fournit une définition du contrôle.</span><span class="sxs-lookup"><span data-stu-id="aaad0-131">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="aaad0-132">Remarks</span><span class="sxs-lookup"><span data-stu-id="aaad0-132">Remarks</span></span>

<span data-ttu-id="aaad0-133">Lorsque vous spécifiez les éléments enfants de l’élément `CustomItem`, gardez à l’esprit les points suivants :</span><span class="sxs-lookup"><span data-stu-id="aaad0-133">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="aaad0-134">Les éléments enfants doivent être ajoutés dans la séquence suivante : `ExpressionBinding`, `NewLine`, `Text` et `Frame`.</span><span class="sxs-lookup"><span data-stu-id="aaad0-134">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="aaad0-135">Il n’existe pas de limite maximale pour le nombre de séquences que vous pouvez spécifier.</span><span class="sxs-lookup"><span data-stu-id="aaad0-135">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="aaad0-136">Dans chaque séquence, il n’existe pas de limite maximale pour le nombre d’éléments `ExpressionBinding` que vous pouvez utiliser.</span><span class="sxs-lookup"><span data-stu-id="aaad0-136">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="aaad0-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aaad0-137">See Also</span></span>

[<span data-ttu-id="aaad0-138">Élément ExpressionBinding pour CustomItem pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="aaad0-138">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="aaad0-139">Élément Frame pour CustomItem pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="aaad0-139">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="aaad0-140">Élément NewLine pour CustomItem pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="aaad0-140">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="aaad0-141">Élément Text pour CustomItem pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="aaad0-141">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="aaad0-142">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="aaad0-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
