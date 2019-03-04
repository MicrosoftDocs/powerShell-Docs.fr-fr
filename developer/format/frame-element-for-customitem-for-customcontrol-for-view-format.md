---
title: Des frames élément pour CustomItem pour CustomControl de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e1a13100-41a4-4847-9f07-458c85783505
caps.latest.revision: 6
ms.openlocfilehash: a7ee550527ec1cb00b4ed83478992c7ab54dbdb6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861705"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="ca287-102">Frame, élément pour CustomItem pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="ca287-102">Frame Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="ca287-103">Définit l’affichage des données, telles que les données le décalage vers la gauche ou droite.</span><span class="sxs-lookup"><span data-stu-id="ca287-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="ca287-104">Cet élément est utilisé lors de la définition d’une vue de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="ca287-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="ca287-105">Élément (Format) élément ViewDefinitions (Format) vue élément (Format) élément CustomControl (Format) CustomEntries élément de configuration pour CustomControl pour élément d’affichage (Format) de CustomEntry pour CustomEntries pour l’élément d’affichage (Format) de CustomItem pour CustomEntry d’élément de Frame CutomControlView (Format) pour CustomItem pour CustomControl de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="ca287-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CutomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ca287-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ca287-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ca287-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="ca287-107">Attributes and Elements</span></span>

<span data-ttu-id="ca287-108">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `Frame` élément.</span><span class="sxs-lookup"><span data-stu-id="ca287-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ca287-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="ca287-109">Attributes</span></span>

<span data-ttu-id="ca287-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="ca287-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ca287-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ca287-111">Child Elements</span></span>

|<span data-ttu-id="ca287-112">Élément</span><span class="sxs-lookup"><span data-stu-id="ca287-112">Element</span></span>|<span data-ttu-id="ca287-113">Description</span><span class="sxs-lookup"><span data-stu-id="ca287-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="ca287-114">Élément requis</span><span class="sxs-lookup"><span data-stu-id="ca287-114">Required Element</span></span>|
|[<span data-ttu-id="ca287-115">Élément de FirstLineHanging</span><span class="sxs-lookup"><span data-stu-id="ca287-115">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="ca287-116">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="ca287-116">Optional element.</span></span><br /><br /> <span data-ttu-id="ca287-117">Spécifie le nombre de caractères la première ligne de données est décalée vers la gauche.</span><span class="sxs-lookup"><span data-stu-id="ca287-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="ca287-118">Élément de FirstLineIndent</span><span class="sxs-lookup"><span data-stu-id="ca287-118">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="ca287-119">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="ca287-119">Optional element.</span></span><br /><br /> <span data-ttu-id="ca287-120">Spécifie le nombre de caractères la première ligne de données est décalée vers la droite.</span><span class="sxs-lookup"><span data-stu-id="ca287-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="ca287-121">Élément de Macintosh</span><span class="sxs-lookup"><span data-stu-id="ca287-121">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="ca287-122">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="ca287-122">Optional element.</span></span><br /><br /> <span data-ttu-id="ca287-123">Spécifie le nombre de caractères les données s’éloigne de la marge de gauche.</span><span class="sxs-lookup"><span data-stu-id="ca287-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="ca287-124">Élément de RightIndent</span><span class="sxs-lookup"><span data-stu-id="ca287-124">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="ca287-125">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="ca287-125">Optional element.</span></span><br /><br /> <span data-ttu-id="ca287-126">Spécifie le nombre de caractères les données s’éloigne de la marge de droite.</span><span class="sxs-lookup"><span data-stu-id="ca287-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ca287-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ca287-127">Parent Elements</span></span>

|<span data-ttu-id="ca287-128">Élément</span><span class="sxs-lookup"><span data-stu-id="ca287-128">Element</span></span>|<span data-ttu-id="ca287-129">Description</span><span class="sxs-lookup"><span data-stu-id="ca287-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ca287-130">Élément CustomItem pour CustomEntry pour la vue (Format)</span><span class="sxs-lookup"><span data-stu-id="ca287-130">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="ca287-131">Définit les données affichées par le contrôle et comment il est affiché.</span><span class="sxs-lookup"><span data-stu-id="ca287-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ca287-132">Remarques</span><span class="sxs-lookup"><span data-stu-id="ca287-132">Remarks</span></span>

<span data-ttu-id="ca287-133">Vous ne pouvez pas spécifier le [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) et [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) éléments dans le même `Frame` élément.</span><span class="sxs-lookup"><span data-stu-id="ca287-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="ca287-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ca287-134">See Also</span></span>

[<span data-ttu-id="ca287-135">Élément de FirstLineHanging</span><span class="sxs-lookup"><span data-stu-id="ca287-135">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="ca287-136">Élément de FirstLineIndent</span><span class="sxs-lookup"><span data-stu-id="ca287-136">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="ca287-137">Élément de Macintosh</span><span class="sxs-lookup"><span data-stu-id="ca287-137">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="ca287-138">Élément de RightIndent</span><span class="sxs-lookup"><span data-stu-id="ca287-138">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="ca287-139">Élément CustomItem pour CustomEntry pour la vue (Format)</span><span class="sxs-lookup"><span data-stu-id="ca287-139">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="ca287-140">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="ca287-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
