---
title: Élément CustomEntry pour CustomControl pour GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2987cb45-f646-45d4-b81b-7871e77af36f
caps.latest.revision: 5
ms.openlocfilehash: dcf4f8b2bbd422067ffdf9b3b4972e279e91edf9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066471"
---
# <a name="customentry-element-for-customcontrol-for-groupby-format"></a><span data-ttu-id="d13b8-102">CustomEntry, élément pour CustomControl pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="d13b8-102">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>

<span data-ttu-id="d13b8-103">Fournit une définition du contrôle.</span><span class="sxs-lookup"><span data-stu-id="d13b8-103">Provides a definition of the control.</span></span> <span data-ttu-id="d13b8-104">Cet élément est utilisé lors de la définition d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="d13b8-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="d13b8-105">Configuration élément (Format) ViewDefinitions (Format) vue (Format) d’élément GroupBy élément pour les éléments de CustomControl affichage (Format) d’élément de CustomEntries GroupBy (Format) pour CustomControl d’élément de CustomEntry GroupBy (Format) pour CustomControl pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="d13b8-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d13b8-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d13b8-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d13b8-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="d13b8-107">Attributes and Elements</span></span>

<span data-ttu-id="d13b8-108">Les sections suivantes décrivent les attributs, éléments enfants et les éléments parents de la `CustomEntry` élément.</span><span class="sxs-lookup"><span data-stu-id="d13b8-108">The following sections describe attributes, child elements, and the parent elements of the `CustomEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d13b8-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="d13b8-109">Attributes</span></span>

<span data-ttu-id="d13b8-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="d13b8-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d13b8-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d13b8-111">Child Elements</span></span>

|<span data-ttu-id="d13b8-112">Élément</span><span class="sxs-lookup"><span data-stu-id="d13b8-112">Element</span></span>|<span data-ttu-id="d13b8-113">Description</span><span class="sxs-lookup"><span data-stu-id="d13b8-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d13b8-114">Élément EntrySelectedBy pour CustomEntry pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="d13b8-114">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="d13b8-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="d13b8-115">Optional element.</span></span><br /><br /> <span data-ttu-id="d13b8-116">Définit les types .NET qui utilisent cette définition de contrôle ou la condition qui doit exister pour cette définition à utiliser.</span><span class="sxs-lookup"><span data-stu-id="d13b8-116">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="d13b8-117">Élément CustomItem pour CustomEntry pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="d13b8-117">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="d13b8-118">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="d13b8-118">Required element.</span></span><br /><br /> <span data-ttu-id="d13b8-119">Définit comment le contrôle affiche les données.</span><span class="sxs-lookup"><span data-stu-id="d13b8-119">Defines how the control displays the data.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d13b8-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d13b8-120">Parent Elements</span></span>

|<span data-ttu-id="d13b8-121">Élément</span><span class="sxs-lookup"><span data-stu-id="d13b8-121">Element</span></span>|<span data-ttu-id="d13b8-122">Description</span><span class="sxs-lookup"><span data-stu-id="d13b8-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d13b8-123">Élément CustomEntries pour CustomControl pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="d13b8-123">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="d13b8-124">Fournit les définitions pour le contrôle.</span><span class="sxs-lookup"><span data-stu-id="d13b8-124">Provides the definitions for the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d13b8-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="d13b8-125">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="d13b8-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d13b8-126">See Also</span></span>

[<span data-ttu-id="d13b8-127">Élément EntrySelectedBy pour CustomEntry pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="d13b8-127">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="d13b8-128">Élément CustomItem pour CustomEntry pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="d13b8-128">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="d13b8-129">Élément CustomEntries pour CustomControl pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="d13b8-129">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="d13b8-130">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="d13b8-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
