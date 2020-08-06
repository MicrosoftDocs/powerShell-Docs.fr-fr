---
title: Élément CustomItem pour CustomEntry pour CustomControl pour View (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 25101c9c156ef91657f51db7044bf9a6653142a2
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785827"
---
# <a name="customitem-element-for-customentry-for-customcontrol-for-view-format"></a><span data-ttu-id="134df-102">CustomItem, élément pour CustomEntry pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="134df-102">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>

<span data-ttu-id="134df-103">Définit les données affichées par l’affichage de contrôle personnalisé et leur mode d’affichage.</span><span class="sxs-lookup"><span data-stu-id="134df-103">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="134df-104">Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="134df-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="134df-105">Élément de configuration (format) élément ViewDefinitions (format) élément de vue (format) élément CustomControl (format) élément CustomEntries pour CustomControl pour View (format) élément CustomEntry pour CustomEntries pour l’élément View (format) CustomItem pour CustomEntry pour View (format)</span><span class="sxs-lookup"><span data-stu-id="134df-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="134df-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="134df-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="134df-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="134df-107">Attributes and Elements</span></span>

<span data-ttu-id="134df-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `CustomItem` élément.</span><span class="sxs-lookup"><span data-stu-id="134df-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="134df-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="134df-109">Attributes</span></span>

<span data-ttu-id="134df-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="134df-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="134df-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="134df-111">Child Elements</span></span>

|<span data-ttu-id="134df-112">Élément</span><span class="sxs-lookup"><span data-stu-id="134df-112">Element</span></span>|<span data-ttu-id="134df-113">Description</span><span class="sxs-lookup"><span data-stu-id="134df-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="134df-114">ExpressionBinding, élément pour CustomItem pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="134df-114">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="134df-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="134df-115">Optional element.</span></span><br /><br /> <span data-ttu-id="134df-116">Définit les données affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="134df-116">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="134df-117">Frame, élément pour CustomItem pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="134df-117">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="134df-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="134df-118">Optional element.</span></span><br /><br /> <span data-ttu-id="134df-119">Définit les données affichées par l’affichage de contrôle personnalisé et leur mode d’affichage.</span><span class="sxs-lookup"><span data-stu-id="134df-119">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="134df-120">Élément NewLine pour CustomItem pour un contrôle personnalisé pour View (format)</span><span class="sxs-lookup"><span data-stu-id="134df-120">NewLine Element for CustomItem for Custom Control for View (Format)</span></span>](./newline-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="134df-121">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="134df-121">Optional element.</span></span><br /><br /> <span data-ttu-id="134df-122">Ajoute une ligne vide à l’affichage du contrôle.</span><span class="sxs-lookup"><span data-stu-id="134df-122">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="134df-123">Élément de texte pour CustomItem pour CustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="134df-123">Text Element for CustomItem for CustomControl for View (Format)</span></span>](./text-element-for-customitem-for-customview-for-view-format.md)|<span data-ttu-id="134df-124">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="134df-124">Optional element.</span></span><br /><br /> <span data-ttu-id="134df-125">Spécifie du texte supplémentaire pour les données affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="134df-125">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="134df-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="134df-126">Parent Elements</span></span>

|<span data-ttu-id="134df-127">Élément</span><span class="sxs-lookup"><span data-stu-id="134df-127">Element</span></span>|<span data-ttu-id="134df-128">Description</span><span class="sxs-lookup"><span data-stu-id="134df-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="134df-129">CustomEntry, élément pour CustomEntries pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="134df-129">CustomEntry Element for CustomEntries for CustomControl for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="134df-130">Fournit une définition de l’affichage de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="134df-130">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="134df-131">Notes</span><span class="sxs-lookup"><span data-stu-id="134df-131">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="134df-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="134df-132">See Also</span></span>

[<span data-ttu-id="134df-133">Élément CustomEntry pour CustomEntries pour View (format)</span><span class="sxs-lookup"><span data-stu-id="134df-133">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="134df-134">ExpressionBinding, élément pour CustomItem pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="134df-134">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="134df-135">Frame, élément pour CustomItem pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="134df-135">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="134df-136">NewLine, élément pour CustomItem pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="134df-136">NewLine Element for CustomItem for CustomControl for View (Format)</span></span>](./newline-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="134df-137">Élément de texte pour CustomItem pour CustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="134df-137">Text Element for CustomItem for CustomControl for View (Format)</span></span>](./text-element-for-customitem-for-customview-for-view-format.md)

[<span data-ttu-id="134df-138">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="134df-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
