---
ms.date: 09/13/2016
ms.topic: reference
title: Frame, élément pour CustomItem pour Controls pour View (Format)
description: Frame, élément pour CustomItem pour Controls pour View (Format)
ms.openlocfilehash: 6f26e19a6894ac213b924108a56cb80f9ffd1143
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652211"
---
# <a name="frame-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="19811-103">Frame, élément pour CustomItem pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="19811-103">Frame Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="19811-104">Définit le mode d’affichage des données, par exemple en décalant les données à gauche ou à droite.</span><span class="sxs-lookup"><span data-stu-id="19811-104">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="19811-105">Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.</span><span class="sxs-lookup"><span data-stu-id="19811-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="19811-106">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) contrôle l’élément (format) Control, élément pour les contrôles pour View (format) CustomControl, élément de Control pour les contrôles pour l’élément View (format) CustomEntries pour CustomControl pour View (format) CustomEntry, élément pour CustomEntries pour les contrôles pour la vue (format) CustomItem, élément pour CustomEntry pour les contrôles pour l’élément Frame (format) pour CustomItem pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="19811-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) Frame Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="19811-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="19811-107">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="19811-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="19811-108">Attributes and Elements</span></span>

<span data-ttu-id="19811-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `Frame` élément.</span><span class="sxs-lookup"><span data-stu-id="19811-109">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="19811-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="19811-110">Attributes</span></span>

<span data-ttu-id="19811-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="19811-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="19811-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="19811-112">Child Elements</span></span>

|<span data-ttu-id="19811-113">Élément</span><span class="sxs-lookup"><span data-stu-id="19811-113">Element</span></span>|<span data-ttu-id="19811-114">Description</span><span class="sxs-lookup"><span data-stu-id="19811-114">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="19811-115">Élément requis</span><span class="sxs-lookup"><span data-stu-id="19811-115">Required Element</span></span>|
|[<span data-ttu-id="19811-116">Élément FirstLineHanging de frame de contrôles de vue (format)</span><span class="sxs-lookup"><span data-stu-id="19811-116">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="19811-117">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="19811-117">Optional element.</span></span><br /><br /> <span data-ttu-id="19811-118">Spécifie le nombre de caractères que la première ligne est décalée vers la gauche.</span><span class="sxs-lookup"><span data-stu-id="19811-118">Specifies how many characters the first line is shifted to the left.</span></span>|
|[<span data-ttu-id="19811-119">Élément FirstLineIndent de frame de contrôles de vue (format)</span><span class="sxs-lookup"><span data-stu-id="19811-119">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="19811-120">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="19811-120">Optional element.</span></span><br /><br /> <span data-ttu-id="19811-121">Spécifie le nombre de caractères que la première ligne est décalée vers la droite.</span><span class="sxs-lookup"><span data-stu-id="19811-121">Specifies how many characters the first line is shifted to the right.</span></span>|
|[<span data-ttu-id="19811-122">LeftIndent, élément de frame de contrôles de vue (format)</span><span class="sxs-lookup"><span data-stu-id="19811-122">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="19811-123">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="19811-123">Optional element.</span></span><br /><br /> <span data-ttu-id="19811-124">Spécifie le nombre de caractères de décalage des données par rapport à la marge de gauche.</span><span class="sxs-lookup"><span data-stu-id="19811-124">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="19811-125">Élément RightIndent du frame des contrôles de vue (format)</span><span class="sxs-lookup"><span data-stu-id="19811-125">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="19811-126">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="19811-126">Optional element.</span></span><br /><br /> <span data-ttu-id="19811-127">Spécifie le nombre de caractères dont les données sont décalées en dehors de la marge de droite.</span><span class="sxs-lookup"><span data-stu-id="19811-127">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="19811-128">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="19811-128">Parent Elements</span></span>

|<span data-ttu-id="19811-129">Élément</span><span class="sxs-lookup"><span data-stu-id="19811-129">Element</span></span>|<span data-ttu-id="19811-130">Description</span><span class="sxs-lookup"><span data-stu-id="19811-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="19811-131">CustomItem, élément pour CustomEntry pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="19811-131">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="19811-132">Définit les données affichées par le contrôle et leur mode d’affichage.</span><span class="sxs-lookup"><span data-stu-id="19811-132">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="19811-133">Notes</span><span class="sxs-lookup"><span data-stu-id="19811-133">Remarks</span></span>

<span data-ttu-id="19811-134">Vous ne pouvez pas spécifier les éléments [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) et [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) dans le même `Frame` élément.</span><span class="sxs-lookup"><span data-stu-id="19811-134">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="19811-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="19811-135">See Also</span></span>

[<span data-ttu-id="19811-136">Élément FirstLineHanging de frame de contrôles de vue (format)</span><span class="sxs-lookup"><span data-stu-id="19811-136">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="19811-137">Élément FirstLineIndent de frame de contrôles de vue (format)</span><span class="sxs-lookup"><span data-stu-id="19811-137">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="19811-138">LeftIndent, élément de frame de contrôles de vue (format)</span><span class="sxs-lookup"><span data-stu-id="19811-138">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="19811-139">Élément RightIndent du frame des contrôles de vue (format)</span><span class="sxs-lookup"><span data-stu-id="19811-139">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="19811-140">CustomItem, élément pour CustomEntry pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="19811-140">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="19811-141">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="19811-141">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
