---
title: Élément CustomEntry pour CustomControl pour GroupBy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4df8e5b96868b3814c6d84fa329950bb5345ef6e
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785912"
---
# <a name="customentry-element-for-customcontrol-for-groupby-format"></a><span data-ttu-id="5c414-102">CustomEntry, élément pour CustomControl pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="5c414-102">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>

<span data-ttu-id="5c414-103">Fournit une définition du contrôle.</span><span class="sxs-lookup"><span data-stu-id="5c414-103">Provides a definition of the control.</span></span> <span data-ttu-id="5c414-104">Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="5c414-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="5c414-105">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément View (format) CustomControl pour GroupBy (format) élément CustomEntries pour CustomControl pour la clause GroupBy (format) CustomEntry élément pour CustomControl pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="5c414-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5c414-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5c414-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5c414-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="5c414-107">Attributes and Elements</span></span>

<span data-ttu-id="5c414-108">Les sections suivantes décrivent les attributs, les éléments enfants et les éléments parents de l' `CustomEntry` élément.</span><span class="sxs-lookup"><span data-stu-id="5c414-108">The following sections describe attributes, child elements, and the parent elements of the `CustomEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5c414-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="5c414-109">Attributes</span></span>

<span data-ttu-id="5c414-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="5c414-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5c414-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5c414-111">Child Elements</span></span>

|<span data-ttu-id="5c414-112">Élément</span><span class="sxs-lookup"><span data-stu-id="5c414-112">Element</span></span>|<span data-ttu-id="5c414-113">Description</span><span class="sxs-lookup"><span data-stu-id="5c414-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5c414-114">EntrySelectedBy, élément pour CustomEntry pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="5c414-114">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="5c414-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="5c414-115">Optional element.</span></span><br /><br /> <span data-ttu-id="5c414-116">Définit les types .NET qui utilisent cette définition de contrôle ou la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="5c414-116">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="5c414-117">CustomItem, élément pour CustomEntry pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="5c414-117">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="5c414-118">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="5c414-118">Required element.</span></span><br /><br /> <span data-ttu-id="5c414-119">Définit le mode d’affichage des données par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="5c414-119">Defines how the control displays the data.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5c414-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5c414-120">Parent Elements</span></span>

|<span data-ttu-id="5c414-121">Élément</span><span class="sxs-lookup"><span data-stu-id="5c414-121">Element</span></span>|<span data-ttu-id="5c414-122">Description</span><span class="sxs-lookup"><span data-stu-id="5c414-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5c414-123">CustomEntries, élément pour CustomControl pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="5c414-123">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="5c414-124">Fournit les définitions pour le contrôle.</span><span class="sxs-lookup"><span data-stu-id="5c414-124">Provides the definitions for the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5c414-125">Notes</span><span class="sxs-lookup"><span data-stu-id="5c414-125">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="5c414-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5c414-126">See Also</span></span>

[<span data-ttu-id="5c414-127">EntrySelectedBy, élément pour CustomEntry pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="5c414-127">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="5c414-128">CustomItem, élément pour CustomEntry pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="5c414-128">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="5c414-129">CustomEntries, élément pour CustomControl pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="5c414-129">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="5c414-130">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="5c414-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
