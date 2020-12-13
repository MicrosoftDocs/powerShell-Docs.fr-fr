---
ms.date: 09/13/2016
ms.topic: reference
title: Frame, élément pour CustomItem pour Controls pour Configuration (Format)
description: Frame, élément pour CustomItem pour Controls pour Configuration (Format)
ms.openlocfilehash: 85d095b9b0c25b68b2353bce56b85333aff91b98
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652234"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="0ae48-103">Frame, élément pour CustomItem pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="0ae48-103">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="0ae48-104">Définit le mode d’affichage des données, par exemple en décalant les données à gauche ou à droite.</span><span class="sxs-lookup"><span data-stu-id="0ae48-104">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="0ae48-105">Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="0ae48-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="0ae48-106">Élément de configuration (format) Controls, élément de configuration (format), élément de contrôle pour la configuration (format) CustomControl, élément de Control pour configuration (format) élément CustomEntries pour CustomControl pour la configuration (format) élément CustomEntry pour CustomControl pour les contrôles de configuration (format) élément CustomItem pour CustomEntry pour les contrôles de l’élément frame de configuration pour la configuration (format)</span><span class="sxs-lookup"><span data-stu-id="0ae48-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0ae48-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0ae48-107">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0ae48-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0ae48-108">Attributes and Elements</span></span>

<span data-ttu-id="0ae48-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `Frame` élément.</span><span class="sxs-lookup"><span data-stu-id="0ae48-109">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0ae48-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="0ae48-110">Attributes</span></span>

<span data-ttu-id="0ae48-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="0ae48-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0ae48-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0ae48-112">Child Elements</span></span>

|<span data-ttu-id="0ae48-113">Élément</span><span class="sxs-lookup"><span data-stu-id="0ae48-113">Element</span></span>|<span data-ttu-id="0ae48-114">Description</span><span class="sxs-lookup"><span data-stu-id="0ae48-114">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="0ae48-115">Élément requis</span><span class="sxs-lookup"><span data-stu-id="0ae48-115">Required Element</span></span>|
|[<span data-ttu-id="0ae48-116">FirstLineHanging, élément pour Frame pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="0ae48-116">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="0ae48-117">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="0ae48-117">Optional element.</span></span><br /><br /> <span data-ttu-id="0ae48-118">Spécifie le nombre de caractères que la première ligne de données est décalée vers la gauche.</span><span class="sxs-lookup"><span data-stu-id="0ae48-118">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="0ae48-119">FirstLineIndent, élément pour Frame pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="0ae48-119">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="0ae48-120">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="0ae48-120">Optional element.</span></span><br /><br /> <span data-ttu-id="0ae48-121">Spécifie le nombre de caractères que la première ligne de données est décalée vers la droite.</span><span class="sxs-lookup"><span data-stu-id="0ae48-121">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="0ae48-122">LeftIndent, élément pour Frame pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="0ae48-122">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="0ae48-123">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="0ae48-123">Optional element.</span></span><br /><br /> <span data-ttu-id="0ae48-124">Spécifie le nombre de caractères de décalage des données par rapport à la marge de gauche.</span><span class="sxs-lookup"><span data-stu-id="0ae48-124">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="0ae48-125">RightIndent, élément pour Frame pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="0ae48-125">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="0ae48-126">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="0ae48-126">Optional element.</span></span><br /><br /> <span data-ttu-id="0ae48-127">Spécifie le nombre de caractères dont les données sont décalées en dehors de la marge de droite.</span><span class="sxs-lookup"><span data-stu-id="0ae48-127">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0ae48-128">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0ae48-128">Parent Elements</span></span>

|<span data-ttu-id="0ae48-129">Élément</span><span class="sxs-lookup"><span data-stu-id="0ae48-129">Element</span></span>|<span data-ttu-id="0ae48-130">Description</span><span class="sxs-lookup"><span data-stu-id="0ae48-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0ae48-131">Élément CustomItem pour CustomEntry pour les contrôles de configuration</span><span class="sxs-lookup"><span data-stu-id="0ae48-131">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="0ae48-132">Définit les données affichées par le contrôle et leur mode d’affichage.</span><span class="sxs-lookup"><span data-stu-id="0ae48-132">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0ae48-133">Notes</span><span class="sxs-lookup"><span data-stu-id="0ae48-133">Remarks</span></span>

<span data-ttu-id="0ae48-134">Vous ne pouvez pas spécifier les éléments [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) et [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) dans le même `Frame` élément.</span><span class="sxs-lookup"><span data-stu-id="0ae48-134">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="0ae48-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0ae48-135">See Also</span></span>

[<span data-ttu-id="0ae48-136">FirstLineHanging, élément pour Frame pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="0ae48-136">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="0ae48-137">FirstLineIndent, élément pour Frame pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="0ae48-137">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="0ae48-138">LeftIndent, élément pour Frame pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="0ae48-138">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="0ae48-139">RightIndent, élément pour Frame pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="0ae48-139">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="0ae48-140">Élément CustomItem pour CustomEntry pour les contrôles de configuration</span><span class="sxs-lookup"><span data-stu-id="0ae48-140">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="0ae48-141">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="0ae48-141">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
