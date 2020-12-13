---
ms.date: 09/13/2016
ms.topic: reference
title: CustomEntries, élément pour CustomControl pour Controls pour View (Format)
description: CustomEntries, élément pour CustomControl pour Controls pour View (Format)
ms.openlocfilehash: 43187294a407d08f765f8c42aba25d13dba6d901
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652380"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-view-format"></a><span data-ttu-id="d54d3-103">CustomEntries, élément pour CustomControl pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="d54d3-103">CustomEntries Element for CustomControl for Controls for View (Format)</span></span>

<span data-ttu-id="d54d3-104">Fournit les définitions pour le contrôle.</span><span class="sxs-lookup"><span data-stu-id="d54d3-104">Provides the definitions for the control.</span></span> <span data-ttu-id="d54d3-105">Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.</span><span class="sxs-lookup"><span data-stu-id="d54d3-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="d54d3-106">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) contrôle l’élément (format) contrôle élément pour les contrôles pour View (format) CustomControl, élément de Control pour les contrôles pour View (format) CustomEntries element pour CustomControl pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="d54d3-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d54d3-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d54d3-107">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d54d3-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d54d3-108">Attributes and Elements</span></span>

<span data-ttu-id="d54d3-109">Les sections suivantes décrivent les attributs, les éléments enfants et les éléments parents de l' `CustomEntries` élément.</span><span class="sxs-lookup"><span data-stu-id="d54d3-109">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="d54d3-110">Il n’existe pas de limite maximale pour le nombre d’éléments enfants qui peuvent être spécifiés.</span><span class="sxs-lookup"><span data-stu-id="d54d3-110">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="d54d3-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="d54d3-111">Attributes</span></span>

<span data-ttu-id="d54d3-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="d54d3-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d54d3-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d54d3-113">Child Elements</span></span>

|<span data-ttu-id="d54d3-114">Élément</span><span class="sxs-lookup"><span data-stu-id="d54d3-114">Element</span></span>|<span data-ttu-id="d54d3-115">Description</span><span class="sxs-lookup"><span data-stu-id="d54d3-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d54d3-116">CustomEntry, élément pour CustomEntries pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="d54d3-116">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="d54d3-117">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="d54d3-117">Required element.</span></span><br /><br /> <span data-ttu-id="d54d3-118">Fournit une définition du contrôle.</span><span class="sxs-lookup"><span data-stu-id="d54d3-118">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d54d3-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d54d3-119">Parent Elements</span></span>

|<span data-ttu-id="d54d3-120">Élément</span><span class="sxs-lookup"><span data-stu-id="d54d3-120">Element</span></span>|<span data-ttu-id="d54d3-121">Description</span><span class="sxs-lookup"><span data-stu-id="d54d3-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d54d3-122">CustomControl, élément pour Control pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="d54d3-122">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="d54d3-123">Définit le contrôle utilisé par la vue.</span><span class="sxs-lookup"><span data-stu-id="d54d3-123">Defines the control used by the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d54d3-124">Notes</span><span class="sxs-lookup"><span data-stu-id="d54d3-124">Remarks</span></span>

<span data-ttu-id="d54d3-125">Dans la plupart des cas, un contrôle n’a qu’une seule définition, qui est spécifiée dans un `CustomEntry` élément unique.</span><span class="sxs-lookup"><span data-stu-id="d54d3-125">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="d54d3-126">Toutefois, il est possible de fournir plusieurs définitions si vous souhaitez utiliser le même contrôle pour afficher différents objets .NET.</span><span class="sxs-lookup"><span data-stu-id="d54d3-126">However, it is possible to provide multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="d54d3-127">Dans ce cas, vous pouvez définir un `CustomEntry` élément pour chaque objet ou ensemble d’objets.</span><span class="sxs-lookup"><span data-stu-id="d54d3-127">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="d54d3-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d54d3-128">See Also</span></span>

[<span data-ttu-id="d54d3-129">CustomEntry, élément pour CustomEntries pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="d54d3-129">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="d54d3-130">CustomControl, élément pour Control pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="d54d3-130">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="d54d3-131">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="d54d3-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
