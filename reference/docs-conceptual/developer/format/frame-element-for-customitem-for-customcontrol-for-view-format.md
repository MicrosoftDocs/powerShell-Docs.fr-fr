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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363638"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="35b46-102">Frame, élément pour CustomItem pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="35b46-102">Frame Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="35b46-103">Définit le mode d’affichage des données, par exemple en décalant les données à gauche ou à droite.</span><span class="sxs-lookup"><span data-stu-id="35b46-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="35b46-104">Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="35b46-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="35b46-105">Élément de configuration (format) élément ViewDefinitions (format) élément de vue (format) élément CustomControl (format) élément CustomEntries pour CustomControl pour View (format) élément CustomEntry pour CustomEntries pour la vue (format) CustomItem, élément de CustomEntry pour l’élément de frame CustomControlView (format) pour CustomItem pour CustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="35b46-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CustomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="35b46-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="35b46-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="35b46-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="35b46-107">Attributes and Elements</span></span>

<span data-ttu-id="35b46-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `Frame`.</span><span class="sxs-lookup"><span data-stu-id="35b46-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="35b46-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="35b46-109">Attributes</span></span>

<span data-ttu-id="35b46-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="35b46-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="35b46-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="35b46-111">Child Elements</span></span>

|<span data-ttu-id="35b46-112">Élément</span><span class="sxs-lookup"><span data-stu-id="35b46-112">Element</span></span>|<span data-ttu-id="35b46-113">Description</span><span class="sxs-lookup"><span data-stu-id="35b46-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="35b46-114">Élément requis</span><span class="sxs-lookup"><span data-stu-id="35b46-114">Required Element</span></span>|
|[<span data-ttu-id="35b46-115">Élément FirstLineHanging</span><span class="sxs-lookup"><span data-stu-id="35b46-115">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="35b46-116">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="35b46-116">Optional element.</span></span><br /><br /> <span data-ttu-id="35b46-117">Spécifie le nombre de caractères que la première ligne de données est décalée vers la gauche.</span><span class="sxs-lookup"><span data-stu-id="35b46-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="35b46-118">Élément FirstLineIndent</span><span class="sxs-lookup"><span data-stu-id="35b46-118">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="35b46-119">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="35b46-119">Optional element.</span></span><br /><br /> <span data-ttu-id="35b46-120">Spécifie le nombre de caractères que la première ligne de données est décalée vers la droite.</span><span class="sxs-lookup"><span data-stu-id="35b46-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="35b46-121">Élément LeftIndent</span><span class="sxs-lookup"><span data-stu-id="35b46-121">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="35b46-122">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="35b46-122">Optional element.</span></span><br /><br /> <span data-ttu-id="35b46-123">Spécifie le nombre de caractères de décalage des données par rapport à la marge de gauche.</span><span class="sxs-lookup"><span data-stu-id="35b46-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="35b46-124">Élément RightIndent</span><span class="sxs-lookup"><span data-stu-id="35b46-124">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="35b46-125">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="35b46-125">Optional element.</span></span><br /><br /> <span data-ttu-id="35b46-126">Spécifie le nombre de caractères dont les données sont décalées en dehors de la marge de droite.</span><span class="sxs-lookup"><span data-stu-id="35b46-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="35b46-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="35b46-127">Parent Elements</span></span>

|<span data-ttu-id="35b46-128">Élément</span><span class="sxs-lookup"><span data-stu-id="35b46-128">Element</span></span>|<span data-ttu-id="35b46-129">Description</span><span class="sxs-lookup"><span data-stu-id="35b46-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="35b46-130">Élément CustomItem pour CustomEntry pour View (format)</span><span class="sxs-lookup"><span data-stu-id="35b46-130">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="35b46-131">Définit les données affichées par le contrôle et leur mode d’affichage.</span><span class="sxs-lookup"><span data-stu-id="35b46-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="35b46-132">Remarks</span><span class="sxs-lookup"><span data-stu-id="35b46-132">Remarks</span></span>

<span data-ttu-id="35b46-133">Vous ne pouvez pas spécifier les éléments [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) et [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) dans le même élément `Frame`.</span><span class="sxs-lookup"><span data-stu-id="35b46-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="35b46-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="35b46-134">See Also</span></span>

[<span data-ttu-id="35b46-135">Élément FirstLineHanging</span><span class="sxs-lookup"><span data-stu-id="35b46-135">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="35b46-136">Élément FirstLineIndent</span><span class="sxs-lookup"><span data-stu-id="35b46-136">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="35b46-137">Élément LeftIndent</span><span class="sxs-lookup"><span data-stu-id="35b46-137">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="35b46-138">Élément RightIndent</span><span class="sxs-lookup"><span data-stu-id="35b46-138">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="35b46-139">Élément CustomItem pour CustomEntry pour View (format)</span><span class="sxs-lookup"><span data-stu-id="35b46-139">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="35b46-140">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="35b46-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
