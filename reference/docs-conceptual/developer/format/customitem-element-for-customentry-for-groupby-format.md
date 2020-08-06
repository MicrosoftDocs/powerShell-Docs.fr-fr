---
title: Élément CustomItem pour CustomEntry pour GroupBy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e8086c5330b6644f83316ad4ae33c33ba40d9eee
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783719"
---
# <a name="customitem-element-for-customentry-for-groupby-format"></a><span data-ttu-id="93cb4-102">CustomItem, élément pour CustomEntry pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="93cb4-102">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="93cb4-103">Définit les données affichées par l’affichage de contrôle personnalisé et leur mode d’affichage.</span><span class="sxs-lookup"><span data-stu-id="93cb4-103">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="93cb4-104">Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="93cb4-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="93cb4-105">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément View (format) CustomControl pour GroupBy (format) élément CustomEntries pour CustomControl pour l’élément CustomItem GroupBy (format) pour CustomEntry pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="93cb4-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="93cb4-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="93cb4-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="93cb4-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="93cb4-107">Attributes and Elements</span></span>

<span data-ttu-id="93cb4-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `CustomItem` élément.</span><span class="sxs-lookup"><span data-stu-id="93cb4-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="93cb4-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="93cb4-109">Attributes</span></span>

<span data-ttu-id="93cb4-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="93cb4-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="93cb4-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="93cb4-111">Child Elements</span></span>

|<span data-ttu-id="93cb4-112">Élément</span><span class="sxs-lookup"><span data-stu-id="93cb4-112">Element</span></span>|<span data-ttu-id="93cb4-113">Description</span><span class="sxs-lookup"><span data-stu-id="93cb4-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="93cb4-114">ExpressionBinding, élément pour CustomItem pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="93cb4-114">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="93cb4-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="93cb4-115">Optional element.</span></span><br /><br /> <span data-ttu-id="93cb4-116">Définit les données affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="93cb4-116">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="93cb4-117">Frame, élément pour CustomItem pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="93cb4-117">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="93cb4-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="93cb4-118">Optional element.</span></span><br /><br /> <span data-ttu-id="93cb4-119">Définit les données affichées par l’affichage de contrôle personnalisé et leur mode d’affichage.</span><span class="sxs-lookup"><span data-stu-id="93cb4-119">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="93cb4-120">NewLine, élément pour CustomItem pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="93cb4-120">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="93cb4-121">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="93cb4-121">Optional element.</span></span><br /><br /> <span data-ttu-id="93cb4-122">Ajoute une ligne vide à l’affichage du contrôle.</span><span class="sxs-lookup"><span data-stu-id="93cb4-122">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="93cb4-123">Text, élément pour CustomItem pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="93cb4-123">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="93cb4-124">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="93cb4-124">Optional element.</span></span><br /><br /> <span data-ttu-id="93cb4-125">Spécifie du texte supplémentaire pour les données affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="93cb4-125">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="93cb4-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="93cb4-126">Parent Elements</span></span>

|<span data-ttu-id="93cb4-127">Élément</span><span class="sxs-lookup"><span data-stu-id="93cb4-127">Element</span></span>|<span data-ttu-id="93cb4-128">Description</span><span class="sxs-lookup"><span data-stu-id="93cb4-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="93cb4-129">CustomEntry, élément pour CustomControl pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="93cb4-129">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="93cb4-130">Fournit une définition de l’affichage de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="93cb4-130">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="93cb4-131">Notes</span><span class="sxs-lookup"><span data-stu-id="93cb4-131">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="93cb4-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="93cb4-132">See Also</span></span>

[<span data-ttu-id="93cb4-133">CustomEntry, élément pour CustomControl pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="93cb4-133">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="93cb4-134">ExpressionBinding, élément pour CustomItem pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="93cb4-134">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="93cb4-135">Frame, élément pour CustomItem pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="93cb4-135">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="93cb4-136">NewLine, élément pour CustomItem pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="93cb4-136">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="93cb4-137">Text, élément pour CustomItem pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="93cb4-137">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="93cb4-138">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="93cb4-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
