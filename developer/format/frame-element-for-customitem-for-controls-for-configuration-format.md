---
title: Des frames élément pour CustomItem pour les contrôles de Configuration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d879c8ce-679d-4622-bc43-c207f6413871
caps.latest.revision: 9
ms.openlocfilehash: b11b154a94daccead57bdfb5e579e1de2c190c09
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862975"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="3e27b-102">Frame, élément pour CustomItem pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="3e27b-102">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="3e27b-103">Définit l’affichage des données, telles que les données le décalage vers la gauche ou droite.</span><span class="sxs-lookup"><span data-stu-id="3e27b-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="3e27b-104">Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="3e27b-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="3e27b-105">Élément de contrôles (Format) d’élément de configuration de l’élément de contrôle de Configuration (Format) pour les contrôles d’élément de CustomControl Configuration (Format) pour le contrôle de l’élément de Configuration (Format) de CustomEntries pour CustomControl pour la Configuration ( Élément CustomEntry de format) pour CustomControl pour les contrôles d’élément de CustomItem Configuration (Format) pour CustomEntry pour les contrôles d’élément de Frame de Configuration pour CustomItem pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="3e27b-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3e27b-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3e27b-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3e27b-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="3e27b-107">Attributes and Elements</span></span>

<span data-ttu-id="3e27b-108">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `Frame` élément.</span><span class="sxs-lookup"><span data-stu-id="3e27b-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3e27b-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="3e27b-109">Attributes</span></span>

<span data-ttu-id="3e27b-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="3e27b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3e27b-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3e27b-111">Child Elements</span></span>

|<span data-ttu-id="3e27b-112">Élément</span><span class="sxs-lookup"><span data-stu-id="3e27b-112">Element</span></span>|<span data-ttu-id="3e27b-113">Description</span><span class="sxs-lookup"><span data-stu-id="3e27b-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="3e27b-114">Élément requis</span><span class="sxs-lookup"><span data-stu-id="3e27b-114">Required Element</span></span>|
|[<span data-ttu-id="3e27b-115">Élément FirstLineHanging pour Frame pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="3e27b-115">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="3e27b-116">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="3e27b-116">Optional element.</span></span><br /><br /> <span data-ttu-id="3e27b-117">Spécifie le nombre de caractères la première ligne de données est décalée vers la gauche.</span><span class="sxs-lookup"><span data-stu-id="3e27b-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="3e27b-118">Élément FirstLineIndent pour Frame pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="3e27b-118">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="3e27b-119">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="3e27b-119">Optional element.</span></span><br /><br /> <span data-ttu-id="3e27b-120">Spécifie le nombre de caractères la première ligne de données est décalée vers la droite.</span><span class="sxs-lookup"><span data-stu-id="3e27b-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="3e27b-121">Élément Macintosh pour Frame pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="3e27b-121">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="3e27b-122">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="3e27b-122">Optional element.</span></span><br /><br /> <span data-ttu-id="3e27b-123">Spécifie le nombre de caractères les données s’éloigne de la marge de gauche.</span><span class="sxs-lookup"><span data-stu-id="3e27b-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="3e27b-124">Élément RightIndent pour Frame pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="3e27b-124">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="3e27b-125">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="3e27b-125">Optional element.</span></span><br /><br /> <span data-ttu-id="3e27b-126">Spécifie le nombre de caractères les données s’éloigne de la marge de droite.</span><span class="sxs-lookup"><span data-stu-id="3e27b-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3e27b-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3e27b-127">Parent Elements</span></span>

|<span data-ttu-id="3e27b-128">Élément</span><span class="sxs-lookup"><span data-stu-id="3e27b-128">Element</span></span>|<span data-ttu-id="3e27b-129">Description</span><span class="sxs-lookup"><span data-stu-id="3e27b-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3e27b-130">Élément CustomItem pour CustomEntry pour les contrôles de Configuration</span><span class="sxs-lookup"><span data-stu-id="3e27b-130">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="3e27b-131">Définit les données affichées par le contrôle et comment il est affiché.</span><span class="sxs-lookup"><span data-stu-id="3e27b-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3e27b-132">Remarques</span><span class="sxs-lookup"><span data-stu-id="3e27b-132">Remarks</span></span>

<span data-ttu-id="3e27b-133">Vous ne pouvez pas spécifier le [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) et [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) éléments dans le même `Frame` élément.</span><span class="sxs-lookup"><span data-stu-id="3e27b-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="3e27b-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3e27b-134">See Also</span></span>

[<span data-ttu-id="3e27b-135">Élément FirstLineHanging pour Frame pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="3e27b-135">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="3e27b-136">Élément FirstLineIndent pour Frame pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="3e27b-136">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="3e27b-137">Élément Macintosh pour Frame pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="3e27b-137">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="3e27b-138">Élément RightIndent pour Frame pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="3e27b-138">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="3e27b-139">Élément CustomItem pour CustomEntry pour les contrôles de Configuration</span><span class="sxs-lookup"><span data-stu-id="3e27b-139">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="3e27b-140">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="3e27b-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
