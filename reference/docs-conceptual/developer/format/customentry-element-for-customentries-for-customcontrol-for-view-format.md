---
title: Élément CustomEntry pour CustomEntries pour CustomControl pour View (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: a13e83ec941bed80eaab02e40131054432fcce00
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785878"
---
# <a name="customentry-element-for-customentries-for-customcontrol-for-view-format"></a><span data-ttu-id="6e333-102">CustomEntry, élément pour CustomEntries pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="6e333-102">CustomEntry Element for CustomEntries for CustomControl for View (Format)</span></span>

<span data-ttu-id="6e333-103">Fournit une définition de l’affichage de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="6e333-103">Provides a definition of the custom control view.</span></span>

<span data-ttu-id="6e333-104">Élément de configuration (format) élément ViewDefinitions (format) élément de vue (format) CustomControl, élément (format) élément CustomEntries pour CustomControl pour View (format) CustomEntry, élément pour CustomEntries pour View (format)</span><span class="sxs-lookup"><span data-stu-id="6e333-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6e333-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6e333-105">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6e333-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="6e333-106">Attributes and Elements</span></span>

<span data-ttu-id="6e333-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `CustomEntry` élément.</span><span class="sxs-lookup"><span data-stu-id="6e333-107">The following sections describe attributes, child elements, and the parent element of the `CustomEntry` element.</span></span> <span data-ttu-id="6e333-108">Vous devez spécifier les éléments affichés par la définition.</span><span class="sxs-lookup"><span data-stu-id="6e333-108">You must specify the items displayed by the definition.</span></span>

### <a name="attributes"></a><span data-ttu-id="6e333-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="6e333-109">Attributes</span></span>

<span data-ttu-id="6e333-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="6e333-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6e333-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6e333-111">Child Elements</span></span>

|<span data-ttu-id="6e333-112">Élément</span><span class="sxs-lookup"><span data-stu-id="6e333-112">Element</span></span>|<span data-ttu-id="6e333-113">Description</span><span class="sxs-lookup"><span data-stu-id="6e333-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6e333-114">Élément EntrySelectedBy pour CustomEntry pour View (format)</span><span class="sxs-lookup"><span data-stu-id="6e333-114">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="6e333-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="6e333-115">Optional element.</span></span><br /><br /> <span data-ttu-id="6e333-116">Définit les types .NET qui utilisent la définition de l’affichage de contrôle personnalisé ou la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="6e333-116">Defines the .NET types that use the definition of the custom control view or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="6e333-117">Élément CustomItem pour CustomEntry pour View (format)</span><span class="sxs-lookup"><span data-stu-id="6e333-117">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="6e333-118">Définit un contrôle pour la définition de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="6e333-118">Defines a control for the custom control definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6e333-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6e333-119">Parent Elements</span></span>

|<span data-ttu-id="6e333-120">Élément</span><span class="sxs-lookup"><span data-stu-id="6e333-120">Element</span></span>|<span data-ttu-id="6e333-121">Description</span><span class="sxs-lookup"><span data-stu-id="6e333-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6e333-122">CustomEntries, élément pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="6e333-122">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="6e333-123">Fournit les définitions de l’affichage de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="6e333-123">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="6e333-124">L’affichage de contrôle personnalisé doit spécifier une ou plusieurs définitions.</span><span class="sxs-lookup"><span data-stu-id="6e333-124">The custom control view must specify one or more definitions.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6e333-125">Notes</span><span class="sxs-lookup"><span data-stu-id="6e333-125">Remarks</span></span>

<span data-ttu-id="6e333-126">Dans la plupart des cas, une seule définition est requise pour chaque affichage de contrôle personnalisé, mais il est possible d’avoir plusieurs définitions si vous souhaitez utiliser la même vue pour afficher différents objets .NET.</span><span class="sxs-lookup"><span data-stu-id="6e333-126">In most cases, only one definition is required for each custom control view, but it is possible to have multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="6e333-127">Dans ce cas, vous pouvez fournir une définition distincte pour chaque objet ou ensemble d’objets.</span><span class="sxs-lookup"><span data-stu-id="6e333-127">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="6e333-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6e333-128">See Also</span></span>

[<span data-ttu-id="6e333-129">CustomControl, élément pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="6e333-129">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="6e333-130">Élément CustomItem pour CustomEntry pour View (format)</span><span class="sxs-lookup"><span data-stu-id="6e333-130">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="6e333-131">Élément EntrySelectedBy pour CustomEntry pour View (format)</span><span class="sxs-lookup"><span data-stu-id="6e333-131">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="6e333-132">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="6e333-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
