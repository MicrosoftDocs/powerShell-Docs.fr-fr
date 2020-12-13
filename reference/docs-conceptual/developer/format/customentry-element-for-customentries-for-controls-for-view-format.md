---
ms.date: 09/13/2016
ms.topic: reference
title: CustomEntry, élément pour CustomEntries pour Controls pour View (Format)
description: CustomEntry, élément pour CustomEntries pour Controls pour View (Format)
ms.openlocfilehash: a525b198c8f595e04dc0804d36b5533b94f43c6b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646088"
---
# <a name="customentry-element-for-customentries-for-controls-for-view-format"></a><span data-ttu-id="dca20-103">CustomEntry, élément pour CustomEntries pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="dca20-103">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>

<span data-ttu-id="dca20-104">Fournit une définition du contrôle.</span><span class="sxs-lookup"><span data-stu-id="dca20-104">Provides a definition of the control.</span></span> <span data-ttu-id="dca20-105">Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.</span><span class="sxs-lookup"><span data-stu-id="dca20-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="dca20-106">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) contrôle l’élément (format) contrôle élément pour les contrôles pour la vue (format) élément CustomControl pour le contrôle des contrôles pour l’élément View (format) CustomEntries pour CustomControl pour la vue (format) élément CustomEntry pour CustomEntries pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="dca20-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="dca20-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dca20-107">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="dca20-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="dca20-108">Attributes and Elements</span></span>

<span data-ttu-id="dca20-109">Les sections suivantes décrivent les attributs, les éléments enfants et les éléments parents de l' `CustomEntry` élément.</span><span class="sxs-lookup"><span data-stu-id="dca20-109">The following sections describe attributes, child elements, and the parent elements of the `CustomEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="dca20-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="dca20-110">Attributes</span></span>

<span data-ttu-id="dca20-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="dca20-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dca20-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="dca20-112">Child Elements</span></span>

|<span data-ttu-id="dca20-113">Élément</span><span class="sxs-lookup"><span data-stu-id="dca20-113">Element</span></span>|<span data-ttu-id="dca20-114">Description</span><span class="sxs-lookup"><span data-stu-id="dca20-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dca20-115">EntrySelectedBy, élément pour CustomEntry pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="dca20-115">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="dca20-116">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="dca20-116">Optional element.</span></span><br /><br /> <span data-ttu-id="dca20-117">Définit les types .NET qui utilisent cette définition de contrôle ou la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="dca20-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="dca20-118">CustomItem, élément pour CustomEntry pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="dca20-118">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="dca20-119">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="dca20-119">Required element.</span></span><br /><br /> <span data-ttu-id="dca20-120">Définit le mode d’affichage des données par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="dca20-120">Defines how the control displays the data.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="dca20-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="dca20-121">Parent Elements</span></span>

|<span data-ttu-id="dca20-122">Élément</span><span class="sxs-lookup"><span data-stu-id="dca20-122">Element</span></span>|<span data-ttu-id="dca20-123">Description</span><span class="sxs-lookup"><span data-stu-id="dca20-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dca20-124">CustomEntries, élément pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="dca20-124">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="dca20-125">Fournit les définitions pour le contrôle.</span><span class="sxs-lookup"><span data-stu-id="dca20-125">Provides the definitions for the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="dca20-126">Notes</span><span class="sxs-lookup"><span data-stu-id="dca20-126">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="dca20-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dca20-127">See Also</span></span>

[<span data-ttu-id="dca20-128">CustomEntries, élément pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="dca20-128">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="dca20-129">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="dca20-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
