---
title: Élément CustomControl de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2edac16c-0b30-4985-ac84-0821aa9a9f6d
caps.latest.revision: 12
ms.openlocfilehash: bd0f7ca4de8dede97d1553cd62884ea45876e0c7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861255"
---
# <a name="customcontrol-element-for-view-format"></a><span data-ttu-id="57533-102">CustomControl, élément pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="57533-102">CustomControl Element for View (Format)</span></span>

<span data-ttu-id="57533-103">Définit un format de contrôle personnalisé pour la vue.</span><span class="sxs-lookup"><span data-stu-id="57533-103">Defines a custom control format for the view.</span></span>

<span data-ttu-id="57533-104">Configuration élément (Format) élément ViewDefinitions (Format) vue (Format) CustomControl élément (Format)</span><span class="sxs-lookup"><span data-stu-id="57533-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="57533-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="57533-105">Syntax</span></span>

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="57533-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="57533-106">Attributes and Elements</span></span>

<span data-ttu-id="57533-107">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `CustomControl` élément.</span><span class="sxs-lookup"><span data-stu-id="57533-107">The following sections describe attributes, child elements, and the parent element of the `CustomControl` element.</span></span> <span data-ttu-id="57533-108">Vous devez spécifier un seul élément enfant.</span><span class="sxs-lookup"><span data-stu-id="57533-108">You must specify one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="57533-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="57533-109">Attributes</span></span>

<span data-ttu-id="57533-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="57533-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="57533-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="57533-111">Child Elements</span></span>

|<span data-ttu-id="57533-112">Élément</span><span class="sxs-lookup"><span data-stu-id="57533-112">Element</span></span>|<span data-ttu-id="57533-113">Description</span><span class="sxs-lookup"><span data-stu-id="57533-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="57533-114">Élément CustomEntries pour CustomControl de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="57533-114">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="57533-115">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="57533-115">Required element.</span></span><br /><br /> <span data-ttu-id="57533-116">Fournit les définitions de la vue de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="57533-116">Provides the definitions of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="57533-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="57533-117">Parent Elements</span></span>

|<span data-ttu-id="57533-118">Élément</span><span class="sxs-lookup"><span data-stu-id="57533-118">Element</span></span>|<span data-ttu-id="57533-119">Description</span><span class="sxs-lookup"><span data-stu-id="57533-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="57533-120">Élément d’affichage (Format)</span><span class="sxs-lookup"><span data-stu-id="57533-120">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="57533-121">Définit une vue qui est utilisée pour afficher un ou plusieurs objets .NET.</span><span class="sxs-lookup"><span data-stu-id="57533-121">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="57533-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="57533-122">Remarks</span></span>

<span data-ttu-id="57533-123">Dans la plupart des cas, qu’une seule définition est requise pour chaque affichage de contrôle, mais il est possible de fournir plusieurs définitions si vous souhaitez utiliser la même vue pour afficher les différents objets .NET.</span><span class="sxs-lookup"><span data-stu-id="57533-123">In most cases, only one definition is required for each control view, but it is possible to provide multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="57533-124">Dans ce cas, vous pouvez fournir une définition séparée pour chaque objet ou un ensemble d’objets.</span><span class="sxs-lookup"><span data-stu-id="57533-124">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="57533-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="57533-125">See Also</span></span>

[<span data-ttu-id="57533-126">Élément CustomEntries pour CustomControl de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="57533-126">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="57533-127">Élément d’affichage (Format)</span><span class="sxs-lookup"><span data-stu-id="57533-127">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="57533-128">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="57533-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
