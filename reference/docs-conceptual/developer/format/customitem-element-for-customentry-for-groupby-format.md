---
title: Élément CustomItem pour CustomEntry pour GroupBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7c517aa-24f5-41ae-b82d-cb0fac81a245
caps.latest.revision: 7
ms.openlocfilehash: 2d821f5e3bc8d0f81ef8a8a040c6f9bcb1658bee
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363878"
---
# <a name="customitem-element-for-customentry-for-groupby-format"></a><span data-ttu-id="2ba0f-102">CustomItem, élément pour CustomEntry pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="2ba0f-102">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="2ba0f-103">Définit les données affichées par l’affichage de contrôle personnalisé et leur mode d’affichage.</span><span class="sxs-lookup"><span data-stu-id="2ba0f-103">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="2ba0f-104">Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="2ba0f-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="2ba0f-105">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément View (format) CustomControl pour GroupBy (format) élément CustomEntries pour CustomControl pour l’élément CustomItem GroupBy (format) pour CustomEntry pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="2ba0f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2ba0f-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ba0f-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2ba0f-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="2ba0f-107">Attributes and Elements</span></span>

<span data-ttu-id="2ba0f-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `CustomItem`.</span><span class="sxs-lookup"><span data-stu-id="2ba0f-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2ba0f-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="2ba0f-109">Attributes</span></span>

<span data-ttu-id="2ba0f-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="2ba0f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2ba0f-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2ba0f-111">Child Elements</span></span>

|<span data-ttu-id="2ba0f-112">Élément</span><span class="sxs-lookup"><span data-stu-id="2ba0f-112">Element</span></span>|<span data-ttu-id="2ba0f-113">Description</span><span class="sxs-lookup"><span data-stu-id="2ba0f-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2ba0f-114">Élément ExpressionBinding pour CustomItem pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="2ba0f-114">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="2ba0f-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="2ba0f-115">Optional element.</span></span><br /><br /> <span data-ttu-id="2ba0f-116">Définit les données affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="2ba0f-116">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="2ba0f-117">Élément Frame pour CustomItem pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="2ba0f-117">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="2ba0f-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="2ba0f-118">Optional element.</span></span><br /><br /> <span data-ttu-id="2ba0f-119">Définit les données affichées par l’affichage de contrôle personnalisé et leur mode d’affichage.</span><span class="sxs-lookup"><span data-stu-id="2ba0f-119">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="2ba0f-120">Élément NewLine pour CustomItem pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="2ba0f-120">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="2ba0f-121">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="2ba0f-121">Optional element.</span></span><br /><br /> <span data-ttu-id="2ba0f-122">Ajoute une ligne vide à l’affichage du contrôle.</span><span class="sxs-lookup"><span data-stu-id="2ba0f-122">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="2ba0f-123">Élément Text pour CustomItem pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="2ba0f-123">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="2ba0f-124">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="2ba0f-124">Optional element.</span></span><br /><br /> <span data-ttu-id="2ba0f-125">Spécifie du texte supplémentaire pour les données affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="2ba0f-125">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2ba0f-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2ba0f-126">Parent Elements</span></span>

|<span data-ttu-id="2ba0f-127">Élément</span><span class="sxs-lookup"><span data-stu-id="2ba0f-127">Element</span></span>|<span data-ttu-id="2ba0f-128">Description</span><span class="sxs-lookup"><span data-stu-id="2ba0f-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2ba0f-129">Élément CustomEntry pour CustomControl pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="2ba0f-129">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="2ba0f-130">Fournit une définition de l’affichage de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="2ba0f-130">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2ba0f-131">Remarks</span><span class="sxs-lookup"><span data-stu-id="2ba0f-131">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="2ba0f-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2ba0f-132">See Also</span></span>

[<span data-ttu-id="2ba0f-133">Élément CustomEntry pour CustomControl pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="2ba0f-133">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="2ba0f-134">Élément ExpressionBinding pour CustomItem pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="2ba0f-134">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="2ba0f-135">Élément Frame pour CustomItem pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="2ba0f-135">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="2ba0f-136">Élément NewLine pour CustomItem pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="2ba0f-136">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="2ba0f-137">Élément Text pour CustomItem pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="2ba0f-137">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="2ba0f-138">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="2ba0f-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
