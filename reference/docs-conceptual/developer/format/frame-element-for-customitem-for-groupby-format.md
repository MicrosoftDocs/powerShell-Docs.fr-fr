---
title: Élément Frame pour CustomItem pour GroupBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab2a5379-299d-4c97-86a2-b639ea890fae
caps.latest.revision: 6
ms.openlocfilehash: 7f9066c0fe0954fadff9dc8f0c35a62c6710f516
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362948"
---
# <a name="frame-element-for-customitem-for-groupby-format"></a><span data-ttu-id="305af-102">Frame, élément pour CustomItem pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="305af-102">Frame Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="305af-103">Définit le mode d’affichage des données, par exemple en décalant les données à gauche ou à droite.</span><span class="sxs-lookup"><span data-stu-id="305af-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="305af-104">Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="305af-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="305af-105">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément View (format) CustomControl pour GroupBy (format) élément CustomEntries pour CustomControl pour l’élément CustomEntry GroupBy (format) pour CustomControl pour GroupBy (format) élément CustomItem pour CustomEntry pour l’élément de frame GroupBy (format) pour CustomItem pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="305af-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) Frame Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="305af-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="305af-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="305af-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="305af-107">Attributes and Elements</span></span>

<span data-ttu-id="305af-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `Frame`.</span><span class="sxs-lookup"><span data-stu-id="305af-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="305af-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="305af-109">Attributes</span></span>

<span data-ttu-id="305af-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="305af-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="305af-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="305af-111">Child Elements</span></span>

|<span data-ttu-id="305af-112">Élément</span><span class="sxs-lookup"><span data-stu-id="305af-112">Element</span></span>|<span data-ttu-id="305af-113">Description</span><span class="sxs-lookup"><span data-stu-id="305af-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="305af-114">Élément requis</span><span class="sxs-lookup"><span data-stu-id="305af-114">Required Element</span></span>|
|[<span data-ttu-id="305af-115">Élément FirstLineHanging pour frame pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="305af-115">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)|<span data-ttu-id="305af-116">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="305af-116">Optional element.</span></span><br /><br /> <span data-ttu-id="305af-117">Spécifie le nombre de caractères que la première ligne de données est décalée vers la gauche.</span><span class="sxs-lookup"><span data-stu-id="305af-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="305af-118">Élément FirstLineIndent pour frame pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="305af-118">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="305af-119">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="305af-119">Optional element.</span></span><br /><br /> <span data-ttu-id="305af-120">Spécifie le nombre de caractères que la première ligne de données est décalée vers la droite.</span><span class="sxs-lookup"><span data-stu-id="305af-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="305af-121">LeftIndent, élément de frame pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="305af-121">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="305af-122">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="305af-122">Optional element.</span></span><br /><br /> <span data-ttu-id="305af-123">Spécifie le nombre de caractères de décalage des données par rapport à la marge de gauche.</span><span class="sxs-lookup"><span data-stu-id="305af-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|<span data-ttu-id="305af-124">[RightIndent, élément de frame pour GroupBy (format)](./rightindent-element-for-frame-for-groupby-format.md) Élément RightIndent</span><span class="sxs-lookup"><span data-stu-id="305af-124">[RightIndent Element for Frame for GroupBy (Format)](./rightindent-element-for-frame-for-groupby-format.md)RightIndent Element</span></span>|<span data-ttu-id="305af-125">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="305af-125">Optional element.</span></span><br /><br /> <span data-ttu-id="305af-126">Spécifie le nombre de caractères dont les données sont décalées en dehors de la marge de droite.</span><span class="sxs-lookup"><span data-stu-id="305af-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="305af-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="305af-127">Parent Elements</span></span>

|<span data-ttu-id="305af-128">Élément</span><span class="sxs-lookup"><span data-stu-id="305af-128">Element</span></span>|<span data-ttu-id="305af-129">Description</span><span class="sxs-lookup"><span data-stu-id="305af-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="305af-130">Élément CustomItem pour CustomEntry pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="305af-130">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="305af-131">Définit les données affichées par le contrôle et leur mode d’affichage.</span><span class="sxs-lookup"><span data-stu-id="305af-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="305af-132">Remarks</span><span class="sxs-lookup"><span data-stu-id="305af-132">Remarks</span></span>

<span data-ttu-id="305af-133">Vous ne pouvez pas spécifier les éléments [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) et [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) dans le même élément `Frame`.</span><span class="sxs-lookup"><span data-stu-id="305af-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="305af-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="305af-134">See Also</span></span>

[<span data-ttu-id="305af-135">Élément FirstLineHanging pour frame pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="305af-135">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="305af-136">Élément FirstLineIndent pour frame pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="305af-136">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="305af-137">LeftIndent, élément de frame pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="305af-137">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="305af-138">RightIndent, élément de frame pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="305af-138">RightIndent Element for Frame for GroupBy (Format)</span></span>](./rightindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="305af-139">Élément CustomItem pour CustomEntry pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="305af-139">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="305af-140">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="305af-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
