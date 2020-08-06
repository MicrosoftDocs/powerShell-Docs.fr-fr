---
title: Élément Frame pour CustomItem pour les contrôles de configuration (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: fa435b8d6b868d2d7c94b7926321d94edc2ec290
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781475"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="13dad-102">Frame, élément pour CustomItem pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="13dad-102">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="13dad-103">Définit le mode d’affichage des données, par exemple en décalant les données à gauche ou à droite.</span><span class="sxs-lookup"><span data-stu-id="13dad-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="13dad-104">Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="13dad-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="13dad-105">Élément de configuration (format) Controls, élément de configuration (format), élément de contrôle pour la configuration (format) CustomControl, élément de Control pour configuration (format) élément CustomEntries pour CustomControl pour la configuration (format) élément CustomEntry pour CustomControl pour les contrôles de configuration (format) élément CustomItem pour CustomEntry pour les contrôles de l’élément frame de configuration pour la configuration (format)</span><span class="sxs-lookup"><span data-stu-id="13dad-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="13dad-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="13dad-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="13dad-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="13dad-107">Attributes and Elements</span></span>

<span data-ttu-id="13dad-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `Frame` élément.</span><span class="sxs-lookup"><span data-stu-id="13dad-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="13dad-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="13dad-109">Attributes</span></span>

<span data-ttu-id="13dad-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="13dad-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="13dad-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="13dad-111">Child Elements</span></span>

|<span data-ttu-id="13dad-112">Élément</span><span class="sxs-lookup"><span data-stu-id="13dad-112">Element</span></span>|<span data-ttu-id="13dad-113">Description</span><span class="sxs-lookup"><span data-stu-id="13dad-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="13dad-114">Élément requis</span><span class="sxs-lookup"><span data-stu-id="13dad-114">Required Element</span></span>|
|[<span data-ttu-id="13dad-115">FirstLineHanging, élément pour Frame pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="13dad-115">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="13dad-116">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="13dad-116">Optional element.</span></span><br /><br /> <span data-ttu-id="13dad-117">Spécifie le nombre de caractères que la première ligne de données est décalée vers la gauche.</span><span class="sxs-lookup"><span data-stu-id="13dad-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="13dad-118">FirstLineIndent, élément pour Frame pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="13dad-118">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="13dad-119">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="13dad-119">Optional element.</span></span><br /><br /> <span data-ttu-id="13dad-120">Spécifie le nombre de caractères que la première ligne de données est décalée vers la droite.</span><span class="sxs-lookup"><span data-stu-id="13dad-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="13dad-121">LeftIndent, élément pour Frame pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="13dad-121">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="13dad-122">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="13dad-122">Optional element.</span></span><br /><br /> <span data-ttu-id="13dad-123">Spécifie le nombre de caractères de décalage des données par rapport à la marge de gauche.</span><span class="sxs-lookup"><span data-stu-id="13dad-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="13dad-124">RightIndent, élément pour Frame pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="13dad-124">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="13dad-125">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="13dad-125">Optional element.</span></span><br /><br /> <span data-ttu-id="13dad-126">Spécifie le nombre de caractères dont les données sont décalées en dehors de la marge de droite.</span><span class="sxs-lookup"><span data-stu-id="13dad-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="13dad-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="13dad-127">Parent Elements</span></span>

|<span data-ttu-id="13dad-128">Élément</span><span class="sxs-lookup"><span data-stu-id="13dad-128">Element</span></span>|<span data-ttu-id="13dad-129">Description</span><span class="sxs-lookup"><span data-stu-id="13dad-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="13dad-130">Élément CustomItem pour CustomEntry pour les contrôles de configuration</span><span class="sxs-lookup"><span data-stu-id="13dad-130">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="13dad-131">Définit les données affichées par le contrôle et leur mode d’affichage.</span><span class="sxs-lookup"><span data-stu-id="13dad-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="13dad-132">Notes</span><span class="sxs-lookup"><span data-stu-id="13dad-132">Remarks</span></span>

<span data-ttu-id="13dad-133">Vous ne pouvez pas spécifier les éléments [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) et [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) dans le même `Frame` élément.</span><span class="sxs-lookup"><span data-stu-id="13dad-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="13dad-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="13dad-134">See Also</span></span>

[<span data-ttu-id="13dad-135">FirstLineHanging, élément pour Frame pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="13dad-135">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="13dad-136">FirstLineIndent, élément pour Frame pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="13dad-136">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="13dad-137">LeftIndent, élément pour Frame pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="13dad-137">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="13dad-138">RightIndent, élément pour Frame pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="13dad-138">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="13dad-139">Élément CustomItem pour CustomEntry pour les contrôles de configuration</span><span class="sxs-lookup"><span data-stu-id="13dad-139">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="13dad-140">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="13dad-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
