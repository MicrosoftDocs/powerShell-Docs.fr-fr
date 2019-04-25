---
title: Élément CustomEntry pour CustomEntries pour CustomControl de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac3c0a25-f2ca-4e28-b3dc-9cb06a76d92a
caps.latest.revision: 11
ms.openlocfilehash: 7804155bffeb1f0df8339f797bf59f8def56a3fc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066445"
---
# <a name="customentry-element-for-customentries-for-customcontrol-for-view-format"></a><span data-ttu-id="8b5ec-102">CustomEntry, élément pour CustomEntries pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="8b5ec-102">CustomEntry Element for CustomEntries for CustomControl for View (Format)</span></span>

<span data-ttu-id="8b5ec-103">Fournit une définition de la vue de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="8b5ec-103">Provides a definition of the custom control view.</span></span>

<span data-ttu-id="8b5ec-104">Élément (Format) élément ViewDefinitions (Format) vue élément (Format) élément CustomControl (Format) CustomEntries élément de configuration pour CustomControl pour élément d’affichage (Format) de CustomEntry pour CustomEntries pour la vue (Format)</span><span class="sxs-lookup"><span data-stu-id="8b5ec-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8b5ec-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8b5ec-105">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8b5ec-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="8b5ec-106">Attributes and Elements</span></span>

<span data-ttu-id="8b5ec-107">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `CustomEntry` élément.</span><span class="sxs-lookup"><span data-stu-id="8b5ec-107">The following sections describe attributes, child elements, and the parent element of the `CustomEntry` element.</span></span> <span data-ttu-id="8b5ec-108">Vous devez spécifier les éléments affichés par la définition.</span><span class="sxs-lookup"><span data-stu-id="8b5ec-108">You must specify the items displayed by the definition.</span></span>

### <a name="attributes"></a><span data-ttu-id="8b5ec-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="8b5ec-109">Attributes</span></span>

<span data-ttu-id="8b5ec-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="8b5ec-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8b5ec-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8b5ec-111">Child Elements</span></span>

|<span data-ttu-id="8b5ec-112">Élément</span><span class="sxs-lookup"><span data-stu-id="8b5ec-112">Element</span></span>|<span data-ttu-id="8b5ec-113">Description</span><span class="sxs-lookup"><span data-stu-id="8b5ec-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8b5ec-114">Élément EntrySelectedBy pour CustomEntry pour la vue (Format)</span><span class="sxs-lookup"><span data-stu-id="8b5ec-114">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="8b5ec-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="8b5ec-115">Optional element.</span></span><br /><br /> <span data-ttu-id="8b5ec-116">Définit les types .NET qui utilisent la définition de la vue de contrôle personnalisé ou de la condition qui doit exister pour cette définition à utiliser.</span><span class="sxs-lookup"><span data-stu-id="8b5ec-116">Defines the .NET types that use the definition of the custom control view or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="8b5ec-117">Élément CustomItem pour CustomEntry pour la vue (Format)</span><span class="sxs-lookup"><span data-stu-id="8b5ec-117">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="8b5ec-118">Définit un contrôle pour la définition du contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="8b5ec-118">Defines a control for the custom control definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8b5ec-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="8b5ec-119">Parent Elements</span></span>

|<span data-ttu-id="8b5ec-120">Élément</span><span class="sxs-lookup"><span data-stu-id="8b5ec-120">Element</span></span>|<span data-ttu-id="8b5ec-121">Description</span><span class="sxs-lookup"><span data-stu-id="8b5ec-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8b5ec-122">Élément CustomEntries pour CustomControl de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="8b5ec-122">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="8b5ec-123">Fournit les définitions de la vue de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="8b5ec-123">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="8b5ec-124">L’affichage de contrôle personnalisé doit spécifier une ou plusieurs définitions.</span><span class="sxs-lookup"><span data-stu-id="8b5ec-124">The custom control view must specify one or more definitions.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8b5ec-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="8b5ec-125">Remarks</span></span>

<span data-ttu-id="8b5ec-126">Dans la plupart des cas, qu’une seule définition est requise pour chaque affichage de contrôle personnalisé, mais il est possible d’avoir plusieurs définitions si vous souhaitez utiliser la même vue pour afficher les différents objets .NET.</span><span class="sxs-lookup"><span data-stu-id="8b5ec-126">In most cases, only one definition is required for each custom control view, but it is possible to have multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="8b5ec-127">Dans ce cas, vous pouvez fournir une définition séparée pour chaque objet ou un ensemble d’objets.</span><span class="sxs-lookup"><span data-stu-id="8b5ec-127">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="8b5ec-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8b5ec-128">See Also</span></span>

[<span data-ttu-id="8b5ec-129">Élément CustomControl de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="8b5ec-129">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="8b5ec-130">Élément CustomItem pour CustomEntry pour la vue (Format)</span><span class="sxs-lookup"><span data-stu-id="8b5ec-130">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="8b5ec-131">Élément EntrySelectedBy pour CustomEntry pour la vue (Format)</span><span class="sxs-lookup"><span data-stu-id="8b5ec-131">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="8b5ec-132">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="8b5ec-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
