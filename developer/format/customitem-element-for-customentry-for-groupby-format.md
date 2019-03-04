---
title: Élément CustomItem pour CustomEntry pour GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7c517aa-24f5-41ae-b82d-cb0fac81a245
caps.latest.revision: 7
ms.openlocfilehash: 2d821f5e3bc8d0f81ef8a8a040c6f9bcb1658bee
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856925"
---
# <a name="customitem-element-for-customentry-for-groupby-format"></a><span data-ttu-id="7a56d-102">CustomItem, élément pour CustomEntry pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7a56d-102">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="7a56d-103">Définit les données affichées par la vue de contrôle personnalisé et comment il est affiché.</span><span class="sxs-lookup"><span data-stu-id="7a56d-103">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="7a56d-104">Cet élément est utilisé lors de la définition d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="7a56d-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="7a56d-105">Configuration élément (Format) ViewDefinitions (Format) vue (Format) d’élément GroupBy élément pour les éléments de CustomControl affichage (Format) d’élément de CustomEntries GroupBy (Format) pour CustomControl d’élément de CustomItem GroupBy (Format) pour CustomEntry pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7a56d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7a56d-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7a56d-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7a56d-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="7a56d-107">Attributes and Elements</span></span>

<span data-ttu-id="7a56d-108">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `CustomItem` élément.</span><span class="sxs-lookup"><span data-stu-id="7a56d-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7a56d-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="7a56d-109">Attributes</span></span>

<span data-ttu-id="7a56d-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="7a56d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7a56d-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7a56d-111">Child Elements</span></span>

|<span data-ttu-id="7a56d-112">Élément</span><span class="sxs-lookup"><span data-stu-id="7a56d-112">Element</span></span>|<span data-ttu-id="7a56d-113">Description</span><span class="sxs-lookup"><span data-stu-id="7a56d-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7a56d-114">Élément ExpressionBinding pour CustomItem pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7a56d-114">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="7a56d-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="7a56d-115">Optional element.</span></span><br /><br /> <span data-ttu-id="7a56d-116">Définit les données qui sont affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="7a56d-116">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="7a56d-117">Élément de frame pour CustomItem pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7a56d-117">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="7a56d-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="7a56d-118">Optional element.</span></span><br /><br /> <span data-ttu-id="7a56d-119">Définit les données affichées par la vue de contrôle personnalisé et comment il est affiché.</span><span class="sxs-lookup"><span data-stu-id="7a56d-119">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="7a56d-120">Élément de saut de ligne pour CustomItem pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7a56d-120">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="7a56d-121">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="7a56d-121">Optional element.</span></span><br /><br /> <span data-ttu-id="7a56d-122">Ajoute une ligne vide à l’affichage du contrôle.</span><span class="sxs-lookup"><span data-stu-id="7a56d-122">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="7a56d-123">Élément de texte pour CustomItem pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7a56d-123">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="7a56d-124">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="7a56d-124">Optional element.</span></span><br /><br /> <span data-ttu-id="7a56d-125">Spécifie le texte supplémentaire pour les données affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="7a56d-125">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7a56d-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7a56d-126">Parent Elements</span></span>

|<span data-ttu-id="7a56d-127">Élément</span><span class="sxs-lookup"><span data-stu-id="7a56d-127">Element</span></span>|<span data-ttu-id="7a56d-128">Description</span><span class="sxs-lookup"><span data-stu-id="7a56d-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7a56d-129">Élément CustomEntry pour CustomControl pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7a56d-129">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="7a56d-130">Fournit une définition de la vue de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="7a56d-130">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7a56d-131">Remarques</span><span class="sxs-lookup"><span data-stu-id="7a56d-131">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="7a56d-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7a56d-132">See Also</span></span>

[<span data-ttu-id="7a56d-133">Élément CustomEntry pour CustomControl pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7a56d-133">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="7a56d-134">Élément ExpressionBinding pour CustomItem pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7a56d-134">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="7a56d-135">Élément de frame pour CustomItem pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7a56d-135">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="7a56d-136">Élément de saut de ligne pour CustomItem pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7a56d-136">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="7a56d-137">Élément de texte pour CustomItem pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7a56d-137">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="7a56d-138">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="7a56d-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
