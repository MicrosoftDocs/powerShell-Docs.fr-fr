---
title: Élément Frame pour CustomItem pour les contrôles pour View (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5729091-78a9-4bc1-abac-210bc20c6dbe
caps.latest.revision: 7
ms.openlocfilehash: f93dc20a9c5f87c14605578062b1e60f5a3d25cf
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363648"
---
# <a name="frame-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="dfde8-102">Frame, élément pour CustomItem pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="dfde8-102">Frame Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="dfde8-103">Définit le mode d’affichage des données, par exemple en décalant les données à gauche ou à droite.</span><span class="sxs-lookup"><span data-stu-id="dfde8-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="dfde8-104">Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.</span><span class="sxs-lookup"><span data-stu-id="dfde8-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="dfde8-105">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) contrôle l’élément (format) Control, élément pour les contrôles pour View (format) CustomControl, élément de Control pour les contrôles pour l’élément View (format) CustomEntries pour CustomControl pour View (format) CustomEntry, élément pour CustomEntries pour les contrôles pour l’élément CustomItem (format) View pour CustomEntry pour les contrôles pour l’élément Frame (format) de la vue pour CustomItem pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="dfde8-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) Frame Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="dfde8-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dfde8-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="dfde8-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="dfde8-107">Attributes and Elements</span></span>

<span data-ttu-id="dfde8-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `Frame`.</span><span class="sxs-lookup"><span data-stu-id="dfde8-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="dfde8-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="dfde8-109">Attributes</span></span>

<span data-ttu-id="dfde8-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="dfde8-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dfde8-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="dfde8-111">Child Elements</span></span>

|<span data-ttu-id="dfde8-112">Élément</span><span class="sxs-lookup"><span data-stu-id="dfde8-112">Element</span></span>|<span data-ttu-id="dfde8-113">Description</span><span class="sxs-lookup"><span data-stu-id="dfde8-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="dfde8-114">Élément requis</span><span class="sxs-lookup"><span data-stu-id="dfde8-114">Required Element</span></span>|
|[<span data-ttu-id="dfde8-115">Élément FirstLineHanging de frame de contrôles de vue (format)</span><span class="sxs-lookup"><span data-stu-id="dfde8-115">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="dfde8-116">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="dfde8-116">Optional element.</span></span><br /><br /> <span data-ttu-id="dfde8-117">Spécifie le nombre de caractères que la première ligne est décalée vers la gauche.</span><span class="sxs-lookup"><span data-stu-id="dfde8-117">Specifies how many characters the first line is shifted to the left.</span></span>|
|[<span data-ttu-id="dfde8-118">Élément FirstLineIndent de frame de contrôles de vue (format)</span><span class="sxs-lookup"><span data-stu-id="dfde8-118">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="dfde8-119">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="dfde8-119">Optional element.</span></span><br /><br /> <span data-ttu-id="dfde8-120">Spécifie le nombre de caractères que la première ligne est décalée vers la droite.</span><span class="sxs-lookup"><span data-stu-id="dfde8-120">Specifies how many characters the first line is shifted to the right.</span></span>|
|[<span data-ttu-id="dfde8-121">LeftIndent, élément de frame de contrôles de vue (format)</span><span class="sxs-lookup"><span data-stu-id="dfde8-121">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="dfde8-122">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="dfde8-122">Optional element.</span></span><br /><br /> <span data-ttu-id="dfde8-123">Spécifie le nombre de caractères de décalage des données par rapport à la marge de gauche.</span><span class="sxs-lookup"><span data-stu-id="dfde8-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="dfde8-124">Élément RightIndent du frame des contrôles de vue (format)</span><span class="sxs-lookup"><span data-stu-id="dfde8-124">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="dfde8-125">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="dfde8-125">Optional element.</span></span><br /><br /> <span data-ttu-id="dfde8-126">Spécifie le nombre de caractères dont les données sont décalées en dehors de la marge de droite.</span><span class="sxs-lookup"><span data-stu-id="dfde8-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="dfde8-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="dfde8-127">Parent Elements</span></span>

|<span data-ttu-id="dfde8-128">Élément</span><span class="sxs-lookup"><span data-stu-id="dfde8-128">Element</span></span>|<span data-ttu-id="dfde8-129">Description</span><span class="sxs-lookup"><span data-stu-id="dfde8-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dfde8-130">Élément CustomItem pour CustomEntry pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="dfde8-130">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="dfde8-131">Définit les données affichées par le contrôle et leur mode d’affichage.</span><span class="sxs-lookup"><span data-stu-id="dfde8-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="dfde8-132">Remarks</span><span class="sxs-lookup"><span data-stu-id="dfde8-132">Remarks</span></span>

<span data-ttu-id="dfde8-133">Vous ne pouvez pas spécifier les éléments [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) et [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) dans le même élément `Frame`.</span><span class="sxs-lookup"><span data-stu-id="dfde8-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="dfde8-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dfde8-134">See Also</span></span>

[<span data-ttu-id="dfde8-135">Élément FirstLineHanging de frame de contrôles de vue (format)</span><span class="sxs-lookup"><span data-stu-id="dfde8-135">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="dfde8-136">Élément FirstLineIndent de frame de contrôles de vue (format)</span><span class="sxs-lookup"><span data-stu-id="dfde8-136">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="dfde8-137">LeftIndent, élément de frame de contrôles de vue (format)</span><span class="sxs-lookup"><span data-stu-id="dfde8-137">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="dfde8-138">Élément RightIndent du frame des contrôles de vue (format)</span><span class="sxs-lookup"><span data-stu-id="dfde8-138">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="dfde8-139">Élément CustomItem pour CustomEntry pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="dfde8-139">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="dfde8-140">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="dfde8-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)