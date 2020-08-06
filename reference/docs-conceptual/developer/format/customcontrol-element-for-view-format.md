---
title: CustomControl, élément de View (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 660e8fd6531862790a2af7ab27a82e073c230693
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786048"
---
# <a name="customcontrol-element-for-view-format"></a><span data-ttu-id="d8d66-102">CustomControl, élément pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="d8d66-102">CustomControl Element for View (Format)</span></span>

<span data-ttu-id="d8d66-103">Définit un format de contrôle personnalisé pour la vue.</span><span class="sxs-lookup"><span data-stu-id="d8d66-103">Defines a custom control format for the view.</span></span>

<span data-ttu-id="d8d66-104">Élément de configuration (format) élément ViewDefinitions (format) élément View (format) CustomControl, élément (format)</span><span class="sxs-lookup"><span data-stu-id="d8d66-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d8d66-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d8d66-105">Syntax</span></span>

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d8d66-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d8d66-106">Attributes and Elements</span></span>

<span data-ttu-id="d8d66-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `CustomControl` élément.</span><span class="sxs-lookup"><span data-stu-id="d8d66-107">The following sections describe attributes, child elements, and the parent element of the `CustomControl` element.</span></span> <span data-ttu-id="d8d66-108">Vous devez spécifier un élément enfant.</span><span class="sxs-lookup"><span data-stu-id="d8d66-108">You must specify one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d8d66-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="d8d66-109">Attributes</span></span>

<span data-ttu-id="d8d66-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="d8d66-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d8d66-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d8d66-111">Child Elements</span></span>

|<span data-ttu-id="d8d66-112">Élément</span><span class="sxs-lookup"><span data-stu-id="d8d66-112">Element</span></span>|<span data-ttu-id="d8d66-113">Description</span><span class="sxs-lookup"><span data-stu-id="d8d66-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d8d66-114">CustomEntries, élément pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="d8d66-114">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="d8d66-115">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="d8d66-115">Required element.</span></span><br /><br /> <span data-ttu-id="d8d66-116">Fournit les définitions de l’affichage de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="d8d66-116">Provides the definitions of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d8d66-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d8d66-117">Parent Elements</span></span>

|<span data-ttu-id="d8d66-118">Élément</span><span class="sxs-lookup"><span data-stu-id="d8d66-118">Element</span></span>|<span data-ttu-id="d8d66-119">Description</span><span class="sxs-lookup"><span data-stu-id="d8d66-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d8d66-120">View, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="d8d66-120">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="d8d66-121">Définit une vue qui est utilisée pour afficher un ou plusieurs objets .NET.</span><span class="sxs-lookup"><span data-stu-id="d8d66-121">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d8d66-122">Notes</span><span class="sxs-lookup"><span data-stu-id="d8d66-122">Remarks</span></span>

<span data-ttu-id="d8d66-123">Dans la plupart des cas, une seule définition est requise pour chaque vue de contrôle, mais il est possible de fournir plusieurs définitions si vous souhaitez utiliser la même vue pour afficher différents objets .NET.</span><span class="sxs-lookup"><span data-stu-id="d8d66-123">In most cases, only one definition is required for each control view, but it is possible to provide multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="d8d66-124">Dans ce cas, vous pouvez fournir une définition distincte pour chaque objet ou ensemble d’objets.</span><span class="sxs-lookup"><span data-stu-id="d8d66-124">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="d8d66-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d8d66-125">See Also</span></span>

[<span data-ttu-id="d8d66-126">CustomEntries, élément pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="d8d66-126">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="d8d66-127">View, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="d8d66-127">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="d8d66-128">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="d8d66-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
