---
ms.date: 09/13/2016
ms.topic: reference
title: Frame, élément pour CustomItem pour CustomControl pour View (Format)
description: Frame, élément pour CustomItem pour CustomControl pour View (Format)
ms.openlocfilehash: 1ffe071bb6c4f590e4c79803a3faff2108c7b636
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652189"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="09969-103">Frame, élément pour CustomItem pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="09969-103">Frame Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="09969-104">Définit le mode d’affichage des données, par exemple en décalant les données à gauche ou à droite.</span><span class="sxs-lookup"><span data-stu-id="09969-104">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="09969-105">Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="09969-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="09969-106">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) CustomControl, élément (format) CustomEntries élément pour CustomControl pour la vue (format) élément CustomEntry pour CustomEntries pour la vue (format) élément CustomItem pour CustomEntry pour CustomControlView (format) élément Frame pour CustomItem pour la vue (format)</span><span class="sxs-lookup"><span data-stu-id="09969-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CustomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="09969-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="09969-107">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="09969-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="09969-108">Attributes and Elements</span></span>

<span data-ttu-id="09969-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `Frame` élément.</span><span class="sxs-lookup"><span data-stu-id="09969-109">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="09969-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="09969-110">Attributes</span></span>

<span data-ttu-id="09969-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="09969-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="09969-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="09969-112">Child Elements</span></span>

|<span data-ttu-id="09969-113">Élément</span><span class="sxs-lookup"><span data-stu-id="09969-113">Element</span></span>|<span data-ttu-id="09969-114">Description</span><span class="sxs-lookup"><span data-stu-id="09969-114">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="09969-115">Élément requis</span><span class="sxs-lookup"><span data-stu-id="09969-115">Required Element</span></span>|
|[<span data-ttu-id="09969-116">Élément FirstLineHanging</span><span class="sxs-lookup"><span data-stu-id="09969-116">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="09969-117">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="09969-117">Optional element.</span></span><br /><br /> <span data-ttu-id="09969-118">Spécifie le nombre de caractères que la première ligne de données est décalée vers la gauche.</span><span class="sxs-lookup"><span data-stu-id="09969-118">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="09969-119">Élément FirstLineIndent</span><span class="sxs-lookup"><span data-stu-id="09969-119">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="09969-120">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="09969-120">Optional element.</span></span><br /><br /> <span data-ttu-id="09969-121">Spécifie le nombre de caractères que la première ligne de données est décalée vers la droite.</span><span class="sxs-lookup"><span data-stu-id="09969-121">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="09969-122">Élément LeftIndent</span><span class="sxs-lookup"><span data-stu-id="09969-122">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="09969-123">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="09969-123">Optional element.</span></span><br /><br /> <span data-ttu-id="09969-124">Spécifie le nombre de caractères de décalage des données par rapport à la marge de gauche.</span><span class="sxs-lookup"><span data-stu-id="09969-124">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="09969-125">Élément RightIndent</span><span class="sxs-lookup"><span data-stu-id="09969-125">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="09969-126">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="09969-126">Optional element.</span></span><br /><br /> <span data-ttu-id="09969-127">Spécifie le nombre de caractères dont les données sont décalées en dehors de la marge de droite.</span><span class="sxs-lookup"><span data-stu-id="09969-127">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="09969-128">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="09969-128">Parent Elements</span></span>

|<span data-ttu-id="09969-129">Élément</span><span class="sxs-lookup"><span data-stu-id="09969-129">Element</span></span>|<span data-ttu-id="09969-130">Description</span><span class="sxs-lookup"><span data-stu-id="09969-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="09969-131">Élément CustomItem pour CustomEntry pour View (format)</span><span class="sxs-lookup"><span data-stu-id="09969-131">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="09969-132">Définit les données affichées par le contrôle et leur mode d’affichage.</span><span class="sxs-lookup"><span data-stu-id="09969-132">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="09969-133">Notes</span><span class="sxs-lookup"><span data-stu-id="09969-133">Remarks</span></span>

<span data-ttu-id="09969-134">Vous ne pouvez pas spécifier les éléments [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) et [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) dans le même `Frame` élément.</span><span class="sxs-lookup"><span data-stu-id="09969-134">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="09969-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="09969-135">See Also</span></span>

[<span data-ttu-id="09969-136">Élément FirstLineHanging</span><span class="sxs-lookup"><span data-stu-id="09969-136">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="09969-137">Élément FirstLineIndent</span><span class="sxs-lookup"><span data-stu-id="09969-137">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="09969-138">Élément LeftIndent</span><span class="sxs-lookup"><span data-stu-id="09969-138">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="09969-139">Élément RightIndent</span><span class="sxs-lookup"><span data-stu-id="09969-139">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="09969-140">Élément CustomItem pour CustomEntry pour View (format)</span><span class="sxs-lookup"><span data-stu-id="09969-140">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="09969-141">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="09969-141">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
