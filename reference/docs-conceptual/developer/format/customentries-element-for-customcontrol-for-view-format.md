---
title: Élément CustomEntries pour CustomControl pour View (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb412831-94f7-4054-b19e-32c1b14c66dd
caps.latest.revision: 11
ms.openlocfilehash: 827baacd22ef258dd9b0c8a383a23fce7d975f7f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364078"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a><span data-ttu-id="04179-102">CustomEntries, élément pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="04179-102">CustomEntries Element for CustomControl for View (Format)</span></span>

<span data-ttu-id="04179-103">Fournit les définitions de l’affichage de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="04179-103">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="04179-104">L’affichage de contrôle personnalisé doit spécifier une ou plusieurs définitions.</span><span class="sxs-lookup"><span data-stu-id="04179-104">The custom control view must specify one or more definitions.</span></span>

<span data-ttu-id="04179-105">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) CustomControl, élément (format) élément CustomEntries pour CustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="04179-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="04179-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04179-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="04179-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="04179-107">Attributes and Elements</span></span>

<span data-ttu-id="04179-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `CustomControlEntries`.</span><span class="sxs-lookup"><span data-stu-id="04179-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlEntries` element.</span></span> <span data-ttu-id="04179-109">Vous devez spécifier un ou plusieurs éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="04179-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="04179-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="04179-110">Attributes</span></span>

<span data-ttu-id="04179-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="04179-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="04179-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="04179-112">Child Elements</span></span>

|<span data-ttu-id="04179-113">Élément</span><span class="sxs-lookup"><span data-stu-id="04179-113">Element</span></span>|<span data-ttu-id="04179-114">Description</span><span class="sxs-lookup"><span data-stu-id="04179-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="04179-115">Élément CustomEntry pour CustomEntries pour View (format)</span><span class="sxs-lookup"><span data-stu-id="04179-115">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="04179-116">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="04179-116">Required element.</span></span><br /><br /> <span data-ttu-id="04179-117">Fournit une définition de l’affichage de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="04179-117">Provides a definition of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="04179-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="04179-118">Parent Elements</span></span>

|<span data-ttu-id="04179-119">Élément</span><span class="sxs-lookup"><span data-stu-id="04179-119">Element</span></span>|<span data-ttu-id="04179-120">Description</span><span class="sxs-lookup"><span data-stu-id="04179-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="04179-121">CustomControl, élément de View (format)</span><span class="sxs-lookup"><span data-stu-id="04179-121">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)|<span data-ttu-id="04179-122">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="04179-122">Required element.</span></span><br /><br /> <span data-ttu-id="04179-123">Définit un format de contrôle personnalisé pour la vue.</span><span class="sxs-lookup"><span data-stu-id="04179-123">Defines a custom control format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="04179-124">Remarks</span><span class="sxs-lookup"><span data-stu-id="04179-124">Remarks</span></span>

<span data-ttu-id="04179-125">Dans la plupart des cas, un contrôle n’a qu’une seule définition, qui est définie dans un élément `CustomEntry` unique.</span><span class="sxs-lookup"><span data-stu-id="04179-125">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="04179-126">Toutefois, il est possible d’avoir plusieurs définitions si vous souhaitez utiliser le même contrôle pour afficher différents objets .NET.</span><span class="sxs-lookup"><span data-stu-id="04179-126">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="04179-127">Dans ce cas, vous pouvez définir un élément `CustomEntry` pour chaque objet ou ensemble d’objets.</span><span class="sxs-lookup"><span data-stu-id="04179-127">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="04179-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="04179-128">See Also</span></span>

[<span data-ttu-id="04179-129">CustomControl, élément de View (format)</span><span class="sxs-lookup"><span data-stu-id="04179-129">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="04179-130">Élément CustomEntry pour CustomEntries pour View (format)</span><span class="sxs-lookup"><span data-stu-id="04179-130">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="04179-131">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="04179-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
