---
title: Élément CustomEntry pour CustomControl pour GroupBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2987cb45-f646-45d4-b81b-7871e77af36f
caps.latest.revision: 5
ms.openlocfilehash: dcf4f8b2bbd422067ffdf9b3b4972e279e91edf9
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364058"
---
# <a name="customentry-element-for-customcontrol-for-groupby-format"></a><span data-ttu-id="fae28-102">CustomEntry, élément pour CustomControl pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="fae28-102">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>

<span data-ttu-id="fae28-103">Fournit une définition du contrôle.</span><span class="sxs-lookup"><span data-stu-id="fae28-103">Provides a definition of the control.</span></span> <span data-ttu-id="fae28-104">Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="fae28-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="fae28-105">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément View (format) CustomControl pour GroupBy (format) élément CustomEntries pour CustomControl pour l’élément CustomEntry GroupBy (format) pour CustomControl pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="fae28-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fae28-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fae28-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fae28-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="fae28-107">Attributes and Elements</span></span>

<span data-ttu-id="fae28-108">Les sections suivantes décrivent les attributs, les éléments enfants et les éléments parents de l’élément `CustomEntry`.</span><span class="sxs-lookup"><span data-stu-id="fae28-108">The following sections describe attributes, child elements, and the parent elements of the `CustomEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fae28-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="fae28-109">Attributes</span></span>

<span data-ttu-id="fae28-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="fae28-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fae28-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="fae28-111">Child Elements</span></span>

|<span data-ttu-id="fae28-112">Élément</span><span class="sxs-lookup"><span data-stu-id="fae28-112">Element</span></span>|<span data-ttu-id="fae28-113">Description</span><span class="sxs-lookup"><span data-stu-id="fae28-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fae28-114">Élément EntrySelectedBy pour CustomEntry pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="fae28-114">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="fae28-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="fae28-115">Optional element.</span></span><br /><br /> <span data-ttu-id="fae28-116">Définit les types .NET qui utilisent cette définition de contrôle ou la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="fae28-116">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="fae28-117">Élément CustomItem pour CustomEntry pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="fae28-117">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="fae28-118">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="fae28-118">Required element.</span></span><br /><br /> <span data-ttu-id="fae28-119">Définit le mode d’affichage des données par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="fae28-119">Defines how the control displays the data.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="fae28-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="fae28-120">Parent Elements</span></span>

|<span data-ttu-id="fae28-121">Élément</span><span class="sxs-lookup"><span data-stu-id="fae28-121">Element</span></span>|<span data-ttu-id="fae28-122">Description</span><span class="sxs-lookup"><span data-stu-id="fae28-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fae28-123">Élément CustomEntries pour CustomControl pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="fae28-123">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="fae28-124">Fournit les définitions pour le contrôle.</span><span class="sxs-lookup"><span data-stu-id="fae28-124">Provides the definitions for the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="fae28-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="fae28-125">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="fae28-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fae28-126">See Also</span></span>

[<span data-ttu-id="fae28-127">Élément EntrySelectedBy pour CustomEntry pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="fae28-127">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="fae28-128">Élément CustomItem pour CustomEntry pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="fae28-128">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="fae28-129">Élément CustomEntries pour CustomControl pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="fae28-129">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="fae28-130">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="fae28-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
