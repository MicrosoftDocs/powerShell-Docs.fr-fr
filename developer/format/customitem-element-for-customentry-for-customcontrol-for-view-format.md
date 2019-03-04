---
title: Élément CustomItem pour CustomEntry pour CustomControl de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98708c1d-6f39-4a76-b454-31153a6ade8c
caps.latest.revision: 12
ms.openlocfilehash: 3c110bd5fe3ef2f790ef136556afa7c29d0b5b29
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856185"
---
# <a name="customitem-element-for-customentry-for-customcontrol-for-view-format"></a><span data-ttu-id="5c463-102">CustomItem, élément pour CustomEntry pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="5c463-102">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>

<span data-ttu-id="5c463-103">Définit les données affichées par la vue de contrôle personnalisé et comment il est affiché.</span><span class="sxs-lookup"><span data-stu-id="5c463-103">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="5c463-104">Cet élément est utilisé lors de la définition d’une vue de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="5c463-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="5c463-105">Élément (Format) élément ViewDefinitions (Format) vue élément (Format) élément CustomControl (Format) CustomEntries élément de configuration pour CustomControl pour élément d’affichage (Format) de CustomEntry pour CustomEntries pour l’élément d’affichage (Format) de CustomItem pour CustomEntry de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="5c463-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5c463-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5c463-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5c463-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="5c463-107">Attributes and Elements</span></span>

<span data-ttu-id="5c463-108">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `CustomItem` élément.</span><span class="sxs-lookup"><span data-stu-id="5c463-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5c463-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="5c463-109">Attributes</span></span>

<span data-ttu-id="5c463-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="5c463-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5c463-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5c463-111">Child Elements</span></span>

|<span data-ttu-id="5c463-112">Élément</span><span class="sxs-lookup"><span data-stu-id="5c463-112">Element</span></span>|<span data-ttu-id="5c463-113">Description</span><span class="sxs-lookup"><span data-stu-id="5c463-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5c463-114">Élément ExpressionBinding pour CustomItem pour CustomControl de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="5c463-114">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="5c463-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="5c463-115">Optional element.</span></span><br /><br /> <span data-ttu-id="5c463-116">Définit les données qui sont affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="5c463-116">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="5c463-117">Élément de frame pour CustomItem pour CustomControl de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="5c463-117">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="5c463-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="5c463-118">Optional element.</span></span><br /><br /> <span data-ttu-id="5c463-119">Définit les données affichées par la vue de contrôle personnalisé et comment il est affiché.</span><span class="sxs-lookup"><span data-stu-id="5c463-119">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="5c463-120">Élément de saut de ligne pour CustomItem pour un contrôle personnalisé pour la vue (Format)</span><span class="sxs-lookup"><span data-stu-id="5c463-120">NewLine Element for CustomItem for Custom Control for View (Format)</span></span>](./newline-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="5c463-121">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="5c463-121">Optional element.</span></span><br /><br /> <span data-ttu-id="5c463-122">Ajoute une ligne vide à l’affichage du contrôle.</span><span class="sxs-lookup"><span data-stu-id="5c463-122">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="5c463-123">Élément de texte pour CustomItem pour CustomControl de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="5c463-123">Text Element for CustomItem for CustomControl for View (Format)</span></span>](./text-element-for-customitem-for-customview-for-view-format.md)|<span data-ttu-id="5c463-124">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="5c463-124">Optional element.</span></span><br /><br /> <span data-ttu-id="5c463-125">Spécifie le texte supplémentaire pour les données affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="5c463-125">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5c463-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5c463-126">Parent Elements</span></span>

|<span data-ttu-id="5c463-127">Élément</span><span class="sxs-lookup"><span data-stu-id="5c463-127">Element</span></span>|<span data-ttu-id="5c463-128">Description</span><span class="sxs-lookup"><span data-stu-id="5c463-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5c463-129">Élément CustomEntry pour CustomEntries pour CustomControl de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="5c463-129">CustomEntry Element for CustomEntries for CustomControl for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="5c463-130">Fournit une définition de la vue de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="5c463-130">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5c463-131">Remarques</span><span class="sxs-lookup"><span data-stu-id="5c463-131">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="5c463-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5c463-132">See Also</span></span>

[<span data-ttu-id="5c463-133">Élément CustomEntry pour CustomEntries pour la vue (Format)</span><span class="sxs-lookup"><span data-stu-id="5c463-133">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="5c463-134">Élément ExpressionBinding pour CustomItem pour CustomControl de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="5c463-134">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="5c463-135">Élément de frame pour CustomItem pour CustomControl de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="5c463-135">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="5c463-136">Élément de saut de ligne pour CustomItem pour CustomControl de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="5c463-136">NewLine Element for CustomItem for CustomControl for View (Format)</span></span>](./newline-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="5c463-137">Élément de texte pour CustomItem pour CustomControl de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="5c463-137">Text Element for CustomItem for CustomControl for View (Format)</span></span>](./text-element-for-customitem-for-customview-for-view-format.md)

[<span data-ttu-id="5c463-138">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="5c463-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
