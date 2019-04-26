---
title: Élément CustomItem pour CustomEntry pour les contrôles de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33cb5350-73ef-4b79-a879-0edf051869e4
caps.latest.revision: 7
ms.openlocfilehash: 174ba6a14819f823ec39f72e49a626e781221d8c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066377"
---
# <a name="customitem-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="4114f-102">CustomItem, élément pour CustomEntry pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="4114f-102">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="4114f-103">Définit les données affichées par le contrôle et comment il est affiché.</span><span class="sxs-lookup"><span data-stu-id="4114f-103">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="4114f-104">Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.</span><span class="sxs-lookup"><span data-stu-id="4114f-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="4114f-105">Élément (Format) élément ViewDefinitions (Format) vue élément (Format) contrôles élément (Format) contrôle élément de configuration pour les contrôles d’élément de CustomControl vue (Format) pour le contrôle pour les contrôles d’élément de CustomEntries vue (Format) pour CustomControl pour l’élément d’affichage (Format) de CustomEntry pour CustomEntries pour les contrôles pour l’élément d’affichage (Format) de CustomItem pour CustomEntry pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="4114f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4114f-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4114f-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...<Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4114f-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="4114f-107">Attributes and Elements</span></span>

<span data-ttu-id="4114f-108">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `CustomItem` élément.</span><span class="sxs-lookup"><span data-stu-id="4114f-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="4114f-109">Pour plus d’informations, consultez la section Notes.</span><span class="sxs-lookup"><span data-stu-id="4114f-109">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="4114f-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="4114f-110">Attributes</span></span>

<span data-ttu-id="4114f-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="4114f-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4114f-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4114f-112">Child Elements</span></span>

|<span data-ttu-id="4114f-113">Élément</span><span class="sxs-lookup"><span data-stu-id="4114f-113">Element</span></span>|<span data-ttu-id="4114f-114">Description</span><span class="sxs-lookup"><span data-stu-id="4114f-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4114f-115">Élément ExpressionBinding pour CustomItem pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="4114f-115">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="4114f-116">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="4114f-116">Optional element.</span></span><br /><br /> <span data-ttu-id="4114f-117">Définit les données qui sont affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="4114f-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="4114f-118">Élément de frame pour CustomItem pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="4114f-118">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="4114f-119">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="4114f-119">Optional element.</span></span><br /><br /> <span data-ttu-id="4114f-120">Définit l’affichage des données, telles que les données le décalage vers la gauche ou droite.</span><span class="sxs-lookup"><span data-stu-id="4114f-120">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="4114f-121">Élément de saut de ligne pour CustomItem pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="4114f-121">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="4114f-122">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="4114f-122">Optional element.</span></span><br /><br /> <span data-ttu-id="4114f-123">Ajoute une ligne vide à l’affichage du contrôle.</span><span class="sxs-lookup"><span data-stu-id="4114f-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="4114f-124">Élément de texte pour CustomItem pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="4114f-124">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="4114f-125">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="4114f-125">Optional element.</span></span><br /><br /> <span data-ttu-id="4114f-126">Ajoute du texte, tels que des parenthèses ou des crochets, à l’affichage du contrôle.</span><span class="sxs-lookup"><span data-stu-id="4114f-126">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4114f-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4114f-127">Parent Elements</span></span>

|<span data-ttu-id="4114f-128">Élément</span><span class="sxs-lookup"><span data-stu-id="4114f-128">Element</span></span>|<span data-ttu-id="4114f-129">Description</span><span class="sxs-lookup"><span data-stu-id="4114f-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4114f-130">Élément CustomEntry pour CustomEntries pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="4114f-130">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="4114f-131">Fournit une définition du contrôle.</span><span class="sxs-lookup"><span data-stu-id="4114f-131">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4114f-132">Remarques</span><span class="sxs-lookup"><span data-stu-id="4114f-132">Remarks</span></span>

<span data-ttu-id="4114f-133">Lorsque vous spécifiez les éléments enfants de le `CustomItem` élément, gardez les points suivants à l’esprit :</span><span class="sxs-lookup"><span data-stu-id="4114f-133">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="4114f-134">Les éléments enfants doivent être ajoutés dans l’ordre suivant : `ExpressionBinding`, `NewLine`, `Text`, et `Frame`.</span><span class="sxs-lookup"><span data-stu-id="4114f-134">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="4114f-135">Il n’existe aucune limite maximale pour le nombre de séquences que vous pouvez spécifier.</span><span class="sxs-lookup"><span data-stu-id="4114f-135">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="4114f-136">Dans chaque séquence, il n’existe aucune limite maximale pour le nombre de `ExpressionBinding` éléments que vous pouvez utiliser.</span><span class="sxs-lookup"><span data-stu-id="4114f-136">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="4114f-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4114f-137">See Also</span></span>

[<span data-ttu-id="4114f-138">Élément ExpressionBinding pour CustomItem pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="4114f-138">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="4114f-139">Élément de frame pour CustomItem pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="4114f-139">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="4114f-140">Élément de saut de ligne pour CustomItem pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="4114f-140">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="4114f-141">Élément de texte pour CustomItem pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="4114f-141">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="4114f-142">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="4114f-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
