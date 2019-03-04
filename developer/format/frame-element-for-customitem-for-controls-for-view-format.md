---
title: Des frames élément pour CustomItem pour les contrôles de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5729091-78a9-4bc1-abac-210bc20c6dbe
caps.latest.revision: 7
ms.openlocfilehash: f93dc20a9c5f87c14605578062b1e60f5a3d25cf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859815"
---
# <a name="frame-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="00c36-102">Frame, élément pour CustomItem pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="00c36-102">Frame Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="00c36-103">Définit l’affichage des données, telles que les données le décalage vers la gauche ou droite.</span><span class="sxs-lookup"><span data-stu-id="00c36-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="00c36-104">Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.</span><span class="sxs-lookup"><span data-stu-id="00c36-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="00c36-105">Élément (Format) élément ViewDefinitions (Format) vue élément (Format) contrôles élément (Format) contrôle élément de configuration pour les contrôles d’élément de CustomControl vue (Format) pour le contrôle pour les contrôles d’élément de CustomEntries vue (Format) pour CustomControl pour l’élément d’affichage (Format) de CustomEntry pour CustomEntries pour les contrôles pour l’élément d’affichage (Format) de CustomItem pour CustomEntry pour les contrôles d’élément de Frame de vue (Format) pour CustomItem pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="00c36-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) Frame Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="00c36-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00c36-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="00c36-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="00c36-107">Attributes and Elements</span></span>

<span data-ttu-id="00c36-108">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `Frame` élément.</span><span class="sxs-lookup"><span data-stu-id="00c36-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="00c36-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="00c36-109">Attributes</span></span>

<span data-ttu-id="00c36-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="00c36-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="00c36-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="00c36-111">Child Elements</span></span>

|<span data-ttu-id="00c36-112">Élément</span><span class="sxs-lookup"><span data-stu-id="00c36-112">Element</span></span>|<span data-ttu-id="00c36-113">Description</span><span class="sxs-lookup"><span data-stu-id="00c36-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="00c36-114">Élément requis</span><span class="sxs-lookup"><span data-stu-id="00c36-114">Required Element</span></span>|
|[<span data-ttu-id="00c36-115">Élément FirstLineHanging du cadre de contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="00c36-115">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="00c36-116">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="00c36-116">Optional element.</span></span><br /><br /> <span data-ttu-id="00c36-117">Spécifie le nombre de caractères la première ligne est décalée vers la gauche.</span><span class="sxs-lookup"><span data-stu-id="00c36-117">Specifies how many characters the first line is shifted to the left.</span></span>|
|[<span data-ttu-id="00c36-118">Élément FirstLineIndent du cadre de contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="00c36-118">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="00c36-119">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="00c36-119">Optional element.</span></span><br /><br /> <span data-ttu-id="00c36-120">Spécifie le nombre de caractères la première ligne est décalée vers la droite.</span><span class="sxs-lookup"><span data-stu-id="00c36-120">Specifies how many characters the first line is shifted to the right.</span></span>|
|[<span data-ttu-id="00c36-121">Élément Macintosh du cadre de contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="00c36-121">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="00c36-122">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="00c36-122">Optional element.</span></span><br /><br /> <span data-ttu-id="00c36-123">Spécifie le nombre de caractères les données s’éloigne de la marge de gauche.</span><span class="sxs-lookup"><span data-stu-id="00c36-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="00c36-124">Élément RightIndent du cadre de contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="00c36-124">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="00c36-125">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="00c36-125">Optional element.</span></span><br /><br /> <span data-ttu-id="00c36-126">Spécifie le nombre de caractères les données s’éloigne de la marge de droite.</span><span class="sxs-lookup"><span data-stu-id="00c36-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="00c36-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="00c36-127">Parent Elements</span></span>

|<span data-ttu-id="00c36-128">Élément</span><span class="sxs-lookup"><span data-stu-id="00c36-128">Element</span></span>|<span data-ttu-id="00c36-129">Description</span><span class="sxs-lookup"><span data-stu-id="00c36-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="00c36-130">Élément CustomItem pour CustomEntry pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="00c36-130">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="00c36-131">Définit les données affichées par le contrôle et comment il est affiché.</span><span class="sxs-lookup"><span data-stu-id="00c36-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="00c36-132">Remarques</span><span class="sxs-lookup"><span data-stu-id="00c36-132">Remarks</span></span>

<span data-ttu-id="00c36-133">Vous ne pouvez pas spécifier le [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) et [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) éléments dans le même `Frame` élément.</span><span class="sxs-lookup"><span data-stu-id="00c36-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="00c36-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="00c36-134">See Also</span></span>

[<span data-ttu-id="00c36-135">Élément FirstLineHanging du cadre de contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="00c36-135">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="00c36-136">Élément FirstLineIndent du cadre de contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="00c36-136">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="00c36-137">Élément Macintosh du cadre de contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="00c36-137">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="00c36-138">Élément RightIndent du cadre de contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="00c36-138">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="00c36-139">Élément CustomItem pour CustomEntry pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="00c36-139">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="00c36-140">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="00c36-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
