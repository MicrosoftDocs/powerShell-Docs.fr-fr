---
title: Élément Frame pour CustomItem pour CustomControl pour View (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e1a13100-41a4-4847-9f07-458c85783505
caps.latest.revision: 6
ms.openlocfilehash: 925ef86e61801f5a66f89dd25e0756f00dd35155
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363638"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="4bbae-102">Frame, élément pour CustomItem pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="4bbae-102">Frame Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="4bbae-103">Définit le mode d’affichage des données, par exemple en décalant les données à gauche ou à droite.</span><span class="sxs-lookup"><span data-stu-id="4bbae-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="4bbae-104">Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="4bbae-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="4bbae-105">Élément de configuration (format) élément ViewDefinitions (format) élément de vue (format) élément CustomControl (format) élément CustomEntries pour CustomControl pour View (format) élément CustomEntry pour CustomEntries pour la vue (format) CustomItem, élément de CustomEntry pour l’élément de frame CustomControlView (format) pour CustomItem pour CustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="4bbae-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CustomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4bbae-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4bbae-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4bbae-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="4bbae-107">Attributes and Elements</span></span>

<span data-ttu-id="4bbae-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `Frame`.</span><span class="sxs-lookup"><span data-stu-id="4bbae-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4bbae-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="4bbae-109">Attributes</span></span>

<span data-ttu-id="4bbae-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="4bbae-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4bbae-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4bbae-111">Child Elements</span></span>

|<span data-ttu-id="4bbae-112">Élément</span><span class="sxs-lookup"><span data-stu-id="4bbae-112">Element</span></span>|<span data-ttu-id="4bbae-113">Description</span><span class="sxs-lookup"><span data-stu-id="4bbae-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="4bbae-114">Élément requis</span><span class="sxs-lookup"><span data-stu-id="4bbae-114">Required Element</span></span>|
|[<span data-ttu-id="4bbae-115">Élément FirstLineHanging</span><span class="sxs-lookup"><span data-stu-id="4bbae-115">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="4bbae-116">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="4bbae-116">Optional element.</span></span><br /><br /> <span data-ttu-id="4bbae-117">Spécifie le nombre de caractères que la première ligne de données est décalée vers la gauche.</span><span class="sxs-lookup"><span data-stu-id="4bbae-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="4bbae-118">Élément FirstLineIndent</span><span class="sxs-lookup"><span data-stu-id="4bbae-118">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="4bbae-119">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="4bbae-119">Optional element.</span></span><br /><br /> <span data-ttu-id="4bbae-120">Spécifie le nombre de caractères que la première ligne de données est décalée vers la droite.</span><span class="sxs-lookup"><span data-stu-id="4bbae-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="4bbae-121">Élément LeftIndent</span><span class="sxs-lookup"><span data-stu-id="4bbae-121">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="4bbae-122">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="4bbae-122">Optional element.</span></span><br /><br /> <span data-ttu-id="4bbae-123">Spécifie le nombre de caractères de décalage des données par rapport à la marge de gauche.</span><span class="sxs-lookup"><span data-stu-id="4bbae-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="4bbae-124">Élément RightIndent</span><span class="sxs-lookup"><span data-stu-id="4bbae-124">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="4bbae-125">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="4bbae-125">Optional element.</span></span><br /><br /> <span data-ttu-id="4bbae-126">Spécifie le nombre de caractères dont les données sont décalées en dehors de la marge de droite.</span><span class="sxs-lookup"><span data-stu-id="4bbae-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4bbae-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4bbae-127">Parent Elements</span></span>

|<span data-ttu-id="4bbae-128">Élément</span><span class="sxs-lookup"><span data-stu-id="4bbae-128">Element</span></span>|<span data-ttu-id="4bbae-129">Description</span><span class="sxs-lookup"><span data-stu-id="4bbae-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4bbae-130">Élément CustomItem pour CustomEntry pour View (format)</span><span class="sxs-lookup"><span data-stu-id="4bbae-130">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="4bbae-131">Définit les données affichées par le contrôle et leur mode d’affichage.</span><span class="sxs-lookup"><span data-stu-id="4bbae-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4bbae-132">Remarks</span><span class="sxs-lookup"><span data-stu-id="4bbae-132">Remarks</span></span>

<span data-ttu-id="4bbae-133">Vous ne pouvez pas spécifier les éléments [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) et [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) dans le même élément `Frame`.</span><span class="sxs-lookup"><span data-stu-id="4bbae-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="4bbae-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4bbae-134">See Also</span></span>

[<span data-ttu-id="4bbae-135">Élément FirstLineHanging</span><span class="sxs-lookup"><span data-stu-id="4bbae-135">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="4bbae-136">Élément FirstLineIndent</span><span class="sxs-lookup"><span data-stu-id="4bbae-136">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="4bbae-137">Élément LeftIndent</span><span class="sxs-lookup"><span data-stu-id="4bbae-137">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="4bbae-138">Élément RightIndent</span><span class="sxs-lookup"><span data-stu-id="4bbae-138">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="4bbae-139">Élément CustomItem pour CustomEntry pour View (format)</span><span class="sxs-lookup"><span data-stu-id="4bbae-139">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="4bbae-140">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="4bbae-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
