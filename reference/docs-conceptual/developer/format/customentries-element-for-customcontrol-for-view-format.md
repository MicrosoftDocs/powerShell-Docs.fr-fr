---
title: Élément CustomEntries pour CustomControl pour View (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c89eb25f6922a92e2c18298d0128c4c2ca93df3d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785963"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a><span data-ttu-id="91fc3-102">CustomEntries, élément pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="91fc3-102">CustomEntries Element for CustomControl for View (Format)</span></span>

<span data-ttu-id="91fc3-103">Fournit les définitions de l’affichage de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="91fc3-103">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="91fc3-104">L’affichage de contrôle personnalisé doit spécifier une ou plusieurs définitions.</span><span class="sxs-lookup"><span data-stu-id="91fc3-104">The custom control view must specify one or more definitions.</span></span>

<span data-ttu-id="91fc3-105">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) CustomControl, élément (format) élément CustomEntries pour CustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="91fc3-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="91fc3-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="91fc3-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="91fc3-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="91fc3-107">Attributes and Elements</span></span>

<span data-ttu-id="91fc3-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `CustomControlEntries` élément.</span><span class="sxs-lookup"><span data-stu-id="91fc3-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlEntries` element.</span></span> <span data-ttu-id="91fc3-109">Vous devez spécifier un ou plusieurs éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="91fc3-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="91fc3-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="91fc3-110">Attributes</span></span>

<span data-ttu-id="91fc3-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="91fc3-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="91fc3-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="91fc3-112">Child Elements</span></span>

|<span data-ttu-id="91fc3-113">Élément</span><span class="sxs-lookup"><span data-stu-id="91fc3-113">Element</span></span>|<span data-ttu-id="91fc3-114">Description</span><span class="sxs-lookup"><span data-stu-id="91fc3-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="91fc3-115">Élément CustomEntry pour CustomEntries pour View (format)</span><span class="sxs-lookup"><span data-stu-id="91fc3-115">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="91fc3-116">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="91fc3-116">Required element.</span></span><br /><br /> <span data-ttu-id="91fc3-117">Fournit une définition de l’affichage de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="91fc3-117">Provides a definition of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="91fc3-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="91fc3-118">Parent Elements</span></span>

|<span data-ttu-id="91fc3-119">Élément</span><span class="sxs-lookup"><span data-stu-id="91fc3-119">Element</span></span>|<span data-ttu-id="91fc3-120">Description</span><span class="sxs-lookup"><span data-stu-id="91fc3-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="91fc3-121">CustomControl, élément pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="91fc3-121">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)|<span data-ttu-id="91fc3-122">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="91fc3-122">Required element.</span></span><br /><br /> <span data-ttu-id="91fc3-123">Définit un format de contrôle personnalisé pour la vue.</span><span class="sxs-lookup"><span data-stu-id="91fc3-123">Defines a custom control format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="91fc3-124">Notes</span><span class="sxs-lookup"><span data-stu-id="91fc3-124">Remarks</span></span>

<span data-ttu-id="91fc3-125">Dans la plupart des cas, un contrôle n’a qu’une seule définition, qui est définie dans un `CustomEntry` élément unique.</span><span class="sxs-lookup"><span data-stu-id="91fc3-125">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="91fc3-126">Toutefois, il est possible d’avoir plusieurs définitions si vous souhaitez utiliser le même contrôle pour afficher différents objets .NET.</span><span class="sxs-lookup"><span data-stu-id="91fc3-126">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="91fc3-127">Dans ce cas, vous pouvez définir un `CustomEntry` élément pour chaque objet ou ensemble d’objets.</span><span class="sxs-lookup"><span data-stu-id="91fc3-127">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="91fc3-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="91fc3-128">See Also</span></span>

[<span data-ttu-id="91fc3-129">CustomControl, élément pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="91fc3-129">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="91fc3-130">Élément CustomEntry pour CustomEntries pour View (format)</span><span class="sxs-lookup"><span data-stu-id="91fc3-130">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="91fc3-131">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="91fc3-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
