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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065561"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="331a8-102">Frame, élément pour CustomItem pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="331a8-102">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="331a8-103">Définit l’affichage des données, telles que les données le décalage vers la gauche ou droite.</span><span class="sxs-lookup"><span data-stu-id="331a8-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="331a8-104">Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="331a8-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="331a8-105">Élément de contrôles (Format) d’élément de configuration de l’élément de contrôle de Configuration (Format) pour les contrôles d’élément de CustomControl Configuration (Format) pour le contrôle de l’élément de Configuration (Format) de CustomEntries pour CustomControl pour la Configuration ( Élément CustomEntry de format) pour CustomControl pour les contrôles d’élément de CustomItem Configuration (Format) pour CustomEntry pour les contrôles d’élément de Frame de Configuration pour CustomItem pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="331a8-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="331a8-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="331a8-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="331a8-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="331a8-107">Attributes and Elements</span></span>

<span data-ttu-id="331a8-108">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `Frame` élément.</span><span class="sxs-lookup"><span data-stu-id="331a8-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="331a8-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="331a8-109">Attributes</span></span>

<span data-ttu-id="331a8-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="331a8-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="331a8-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="331a8-111">Child Elements</span></span>

|<span data-ttu-id="331a8-112">Élément</span><span class="sxs-lookup"><span data-stu-id="331a8-112">Element</span></span>|<span data-ttu-id="331a8-113">Description</span><span class="sxs-lookup"><span data-stu-id="331a8-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="331a8-114">Élément requis</span><span class="sxs-lookup"><span data-stu-id="331a8-114">Required Element</span></span>|
|[<span data-ttu-id="331a8-115">Élément FirstLineHanging pour Frame pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="331a8-115">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="331a8-116">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="331a8-116">Optional element.</span></span><br /><br /> <span data-ttu-id="331a8-117">Spécifie le nombre de caractères la première ligne de données est décalée vers la gauche.</span><span class="sxs-lookup"><span data-stu-id="331a8-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="331a8-118">Élément FirstLineIndent pour Frame pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="331a8-118">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="331a8-119">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="331a8-119">Optional element.</span></span><br /><br /> <span data-ttu-id="331a8-120">Spécifie le nombre de caractères la première ligne de données est décalée vers la droite.</span><span class="sxs-lookup"><span data-stu-id="331a8-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="331a8-121">Élément Macintosh pour Frame pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="331a8-121">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="331a8-122">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="331a8-122">Optional element.</span></span><br /><br /> <span data-ttu-id="331a8-123">Spécifie le nombre de caractères les données s’éloigne de la marge de gauche.</span><span class="sxs-lookup"><span data-stu-id="331a8-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="331a8-124">Élément RightIndent pour Frame pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="331a8-124">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="331a8-125">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="331a8-125">Optional element.</span></span><br /><br /> <span data-ttu-id="331a8-126">Spécifie le nombre de caractères les données s’éloigne de la marge de droite.</span><span class="sxs-lookup"><span data-stu-id="331a8-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="331a8-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="331a8-127">Parent Elements</span></span>

|<span data-ttu-id="331a8-128">Élément</span><span class="sxs-lookup"><span data-stu-id="331a8-128">Element</span></span>|<span data-ttu-id="331a8-129">Description</span><span class="sxs-lookup"><span data-stu-id="331a8-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="331a8-130">Élément CustomItem pour CustomEntry pour les contrôles de Configuration</span><span class="sxs-lookup"><span data-stu-id="331a8-130">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="331a8-131">Définit les données affichées par le contrôle et comment il est affiché.</span><span class="sxs-lookup"><span data-stu-id="331a8-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="331a8-132">Remarques</span><span class="sxs-lookup"><span data-stu-id="331a8-132">Remarks</span></span>

<span data-ttu-id="331a8-133">Vous ne pouvez pas spécifier le [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) et [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) éléments dans le même `Frame` élément.</span><span class="sxs-lookup"><span data-stu-id="331a8-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="331a8-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="331a8-134">See Also</span></span>

[<span data-ttu-id="331a8-135">Élément FirstLineHanging pour Frame pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="331a8-135">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="331a8-136">Élément FirstLineIndent pour Frame pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="331a8-136">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="331a8-137">Élément Macintosh pour Frame pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="331a8-137">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="331a8-138">Élément RightIndent pour Frame pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="331a8-138">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="331a8-139">Élément CustomItem pour CustomEntry pour les contrôles de Configuration</span><span class="sxs-lookup"><span data-stu-id="331a8-139">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="331a8-140">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="331a8-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
