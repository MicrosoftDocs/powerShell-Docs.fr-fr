---
ms.date: 09/13/2016
ms.topic: reference
title: Frame, élément pour CustomItem pour GroupBy (Format)
description: Frame, élément pour CustomItem pour GroupBy (Format)
ms.openlocfilehash: 86b51766974ebfcae06583ade237a77c6db92866
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652171"
---
# <a name="frame-element-for-customitem-for-groupby-format"></a><span data-ttu-id="7d882-103">Frame, élément pour CustomItem pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7d882-103">Frame Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="7d882-104">Définit le mode d’affichage des données, par exemple en décalant les données à gauche ou à droite.</span><span class="sxs-lookup"><span data-stu-id="7d882-104">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="7d882-105">Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="7d882-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="7d882-106">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément View (format) CustomControl pour GroupBy (format) élément CustomEntries pour CustomControl pour la clause GroupBy (format) CustomEntry élément pour CustomControl pour GroupBy (format) CustomItem élément pour CustomEntry pour l’élément de cadre GroupBy (format) pour l’élément CustomItem pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="7d882-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) Frame Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7d882-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d882-107">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7d882-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7d882-108">Attributes and Elements</span></span>

<span data-ttu-id="7d882-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `Frame` élément.</span><span class="sxs-lookup"><span data-stu-id="7d882-109">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7d882-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="7d882-110">Attributes</span></span>

<span data-ttu-id="7d882-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="7d882-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7d882-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7d882-112">Child Elements</span></span>

|<span data-ttu-id="7d882-113">Élément</span><span class="sxs-lookup"><span data-stu-id="7d882-113">Element</span></span>|<span data-ttu-id="7d882-114">Description</span><span class="sxs-lookup"><span data-stu-id="7d882-114">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="7d882-115">Élément requis</span><span class="sxs-lookup"><span data-stu-id="7d882-115">Required Element</span></span>|
|[<span data-ttu-id="7d882-116">FirstLineHanging, élément pour Frame pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7d882-116">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)|<span data-ttu-id="7d882-117">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="7d882-117">Optional element.</span></span><br /><br /> <span data-ttu-id="7d882-118">Spécifie le nombre de caractères que la première ligne de données est décalée vers la gauche.</span><span class="sxs-lookup"><span data-stu-id="7d882-118">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="7d882-119">FirstLineIndent, élément pour Frame pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7d882-119">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="7d882-120">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="7d882-120">Optional element.</span></span><br /><br /> <span data-ttu-id="7d882-121">Spécifie le nombre de caractères que la première ligne de données est décalée vers la droite.</span><span class="sxs-lookup"><span data-stu-id="7d882-121">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="7d882-122">LeftIndent, élément pour Frame pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7d882-122">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="7d882-123">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="7d882-123">Optional element.</span></span><br /><br /> <span data-ttu-id="7d882-124">Spécifie le nombre de caractères de décalage des données par rapport à la marge de gauche.</span><span class="sxs-lookup"><span data-stu-id="7d882-124">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|<span data-ttu-id="7d882-125">[RightIndent, élément de frame pour GroupBy (format)](./rightindent-element-for-frame-for-groupby-format.md) Élément RightIndent</span><span class="sxs-lookup"><span data-stu-id="7d882-125">[RightIndent Element for Frame for GroupBy (Format)](./rightindent-element-for-frame-for-groupby-format.md)RightIndent Element</span></span>|<span data-ttu-id="7d882-126">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="7d882-126">Optional element.</span></span><br /><br /> <span data-ttu-id="7d882-127">Spécifie le nombre de caractères dont les données sont décalées en dehors de la marge de droite.</span><span class="sxs-lookup"><span data-stu-id="7d882-127">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7d882-128">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7d882-128">Parent Elements</span></span>

|<span data-ttu-id="7d882-129">Élément</span><span class="sxs-lookup"><span data-stu-id="7d882-129">Element</span></span>|<span data-ttu-id="7d882-130">Description</span><span class="sxs-lookup"><span data-stu-id="7d882-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7d882-131">CustomItem, élément pour CustomEntry pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7d882-131">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="7d882-132">Définit les données affichées par le contrôle et leur mode d’affichage.</span><span class="sxs-lookup"><span data-stu-id="7d882-132">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7d882-133">Notes</span><span class="sxs-lookup"><span data-stu-id="7d882-133">Remarks</span></span>

<span data-ttu-id="7d882-134">Vous ne pouvez pas spécifier les éléments [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) et [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) dans le même `Frame` élément.</span><span class="sxs-lookup"><span data-stu-id="7d882-134">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="7d882-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7d882-135">See Also</span></span>

[<span data-ttu-id="7d882-136">FirstLineHanging, élément pour Frame pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7d882-136">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="7d882-137">FirstLineIndent, élément pour Frame pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7d882-137">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="7d882-138">LeftIndent, élément pour Frame pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7d882-138">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="7d882-139">RightIndent, élément pour Frame pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7d882-139">RightIndent Element for Frame for GroupBy (Format)</span></span>](./rightindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="7d882-140">CustomItem, élément pour CustomEntry pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7d882-140">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="7d882-141">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="7d882-141">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
