---
ms.date: 09/13/2016
ms.topic: reference
title: CustomEntries, élément pour CustomControl pour GroupBy (Format)
description: CustomEntries, élément pour CustomControl pour GroupBy (Format)
ms.openlocfilehash: cde59d38b83930cb64a3a0040891783e4ab96723
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666788"
---
# <a name="customentries-element-for-customcontrol-for-groupby-format"></a><span data-ttu-id="602e8-103">CustomEntries, élément pour CustomControl pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="602e8-103">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

<span data-ttu-id="602e8-104">Fournit les définitions pour le contrôle.</span><span class="sxs-lookup"><span data-stu-id="602e8-104">Provides the definitions for the control.</span></span> <span data-ttu-id="602e8-105">Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="602e8-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="602e8-106">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour View (format) CustomControl, élément pour GroupBy (format) élément CustomEntries pour CustomControl pour la clause GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="602e8-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="602e8-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="602e8-107">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="602e8-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="602e8-108">Attributes and Elements</span></span>

<span data-ttu-id="602e8-109">Les sections suivantes décrivent les attributs, les éléments enfants et les éléments parents de l' `CustomEntries` élément.</span><span class="sxs-lookup"><span data-stu-id="602e8-109">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="602e8-110">Il n’existe pas de limite maximale pour le nombre d’éléments enfants qui peuvent être spécifiés.</span><span class="sxs-lookup"><span data-stu-id="602e8-110">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="602e8-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="602e8-111">Attributes</span></span>

<span data-ttu-id="602e8-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="602e8-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="602e8-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="602e8-113">Child Elements</span></span>

|<span data-ttu-id="602e8-114">Élément</span><span class="sxs-lookup"><span data-stu-id="602e8-114">Element</span></span>|<span data-ttu-id="602e8-115">Description</span><span class="sxs-lookup"><span data-stu-id="602e8-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="602e8-116">CustomEntry, élément pour CustomControl pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="602e8-116">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="602e8-117">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="602e8-117">Required element.</span></span><br /><br /> <span data-ttu-id="602e8-118">Fournit une définition du contrôle.</span><span class="sxs-lookup"><span data-stu-id="602e8-118">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="602e8-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="602e8-119">Parent Elements</span></span>

|<span data-ttu-id="602e8-120">Élément</span><span class="sxs-lookup"><span data-stu-id="602e8-120">Element</span></span>|<span data-ttu-id="602e8-121">Description</span><span class="sxs-lookup"><span data-stu-id="602e8-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="602e8-122">CustomControl, élément pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="602e8-122">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="602e8-123">Définit le contrôle personnalisé qui affiche le nouveau groupe.</span><span class="sxs-lookup"><span data-stu-id="602e8-123">Defines the custom control that displays the new group.</span></span>|

## <a name="remarks"></a><span data-ttu-id="602e8-124">Notes</span><span class="sxs-lookup"><span data-stu-id="602e8-124">Remarks</span></span>

<span data-ttu-id="602e8-125">Dans la plupart des cas, un contrôle n’a qu’une seule définition, qui est spécifiée dans un `CustomEntry` élément unique.</span><span class="sxs-lookup"><span data-stu-id="602e8-125">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="602e8-126">Toutefois, il est possible de fournir plusieurs définitions si vous souhaitez utiliser le même contrôle pour afficher des groupes différents.</span><span class="sxs-lookup"><span data-stu-id="602e8-126">However, it is possible to provide multiple definitions if you want to use the same control to display different groups.</span></span> <span data-ttu-id="602e8-127">Dans ce cas, vous pouvez définir un `CustomEntry` élément pour un groupe.</span><span class="sxs-lookup"><span data-stu-id="602e8-127">In those cases, you can define a `CustomEntry` element for a group.</span></span>

## <a name="see-also"></a><span data-ttu-id="602e8-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="602e8-128">See Also</span></span>

[<span data-ttu-id="602e8-129">CustomEntry, élément pour CustomEntries pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="602e8-129">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="602e8-130">CustomControl, élément pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="602e8-130">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="602e8-131">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="602e8-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
