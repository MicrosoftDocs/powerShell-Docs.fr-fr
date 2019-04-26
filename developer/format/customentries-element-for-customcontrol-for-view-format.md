---
title: Élément CustomEntries pour CustomControl de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb412831-94f7-4054-b19e-32c1b14c66dd
caps.latest.revision: 11
ms.openlocfilehash: 827baacd22ef258dd9b0c8a383a23fce7d975f7f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066513"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a><span data-ttu-id="0506e-102">CustomEntries, élément pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="0506e-102">CustomEntries Element for CustomControl for View (Format)</span></span>

<span data-ttu-id="0506e-103">Fournit les définitions de la vue de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="0506e-103">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="0506e-104">L’affichage de contrôle personnalisé doit spécifier une ou plusieurs définitions.</span><span class="sxs-lookup"><span data-stu-id="0506e-104">The custom control view must specify one or more definitions.</span></span>

<span data-ttu-id="0506e-105">Élément (Format) élément ViewDefinitions (Format) vue élément (Format) élément CustomControl (Format) CustomEntries élément de configuration pour CustomControl de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="0506e-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0506e-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0506e-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0506e-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="0506e-107">Attributes and Elements</span></span>

<span data-ttu-id="0506e-108">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `CustomControlEntries` élément.</span><span class="sxs-lookup"><span data-stu-id="0506e-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlEntries` element.</span></span> <span data-ttu-id="0506e-109">Vous devez spécifier un ou plusieurs éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="0506e-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="0506e-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="0506e-110">Attributes</span></span>

<span data-ttu-id="0506e-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="0506e-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0506e-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0506e-112">Child Elements</span></span>

|<span data-ttu-id="0506e-113">Élément</span><span class="sxs-lookup"><span data-stu-id="0506e-113">Element</span></span>|<span data-ttu-id="0506e-114">Description</span><span class="sxs-lookup"><span data-stu-id="0506e-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0506e-115">Élément CustomEntry pour CustomEntries pour la vue (Format)</span><span class="sxs-lookup"><span data-stu-id="0506e-115">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="0506e-116">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="0506e-116">Required element.</span></span><br /><br /> <span data-ttu-id="0506e-117">Fournit une définition de la vue de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="0506e-117">Provides a definition of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0506e-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0506e-118">Parent Elements</span></span>

|<span data-ttu-id="0506e-119">Élément</span><span class="sxs-lookup"><span data-stu-id="0506e-119">Element</span></span>|<span data-ttu-id="0506e-120">Description</span><span class="sxs-lookup"><span data-stu-id="0506e-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0506e-121">Élément CustomControl de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="0506e-121">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)|<span data-ttu-id="0506e-122">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="0506e-122">Required element.</span></span><br /><br /> <span data-ttu-id="0506e-123">Définit un format de contrôle personnalisé pour la vue.</span><span class="sxs-lookup"><span data-stu-id="0506e-123">Defines a custom control format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0506e-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="0506e-124">Remarks</span></span>

<span data-ttu-id="0506e-125">Dans la plupart des cas, un contrôle n'a qu’une seule définition, ce qui est définie dans un seul `CustomEntry` élément.</span><span class="sxs-lookup"><span data-stu-id="0506e-125">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="0506e-126">Toutefois, il est possible d’avoir plusieurs définitions si vous souhaitez utiliser le même contrôle pour afficher les différents objets .NET.</span><span class="sxs-lookup"><span data-stu-id="0506e-126">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="0506e-127">Dans ce cas, vous pouvez définir un `CustomEntry` élément pour chaque objet ou un ensemble d’objets.</span><span class="sxs-lookup"><span data-stu-id="0506e-127">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="0506e-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0506e-128">See Also</span></span>

[<span data-ttu-id="0506e-129">Élément CustomControl de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="0506e-129">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="0506e-130">Élément CustomEntry pour CustomEntries pour la vue (Format)</span><span class="sxs-lookup"><span data-stu-id="0506e-130">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="0506e-131">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="0506e-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
