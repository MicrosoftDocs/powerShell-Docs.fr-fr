---
title: Élément CustomEntry pour CustomEntries pour les contrôles pour View (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4fc960ab803580f684ce0f224b1db4d7d4af1720
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785895"
---
# <a name="customentry-element-for-customentries-for-controls-for-view-format"></a><span data-ttu-id="29bee-102">CustomEntry, élément pour CustomEntries pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="29bee-102">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>

<span data-ttu-id="29bee-103">Fournit une définition du contrôle.</span><span class="sxs-lookup"><span data-stu-id="29bee-103">Provides a definition of the control.</span></span> <span data-ttu-id="29bee-104">Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.</span><span class="sxs-lookup"><span data-stu-id="29bee-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="29bee-105">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) contrôle l’élément (format) contrôle élément pour les contrôles pour la vue (format) élément CustomControl pour le contrôle des contrôles pour l’élément View (format) CustomEntries pour CustomControl pour la vue (format) élément CustomEntry pour CustomEntries pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="29bee-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="29bee-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29bee-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="29bee-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="29bee-107">Attributes and Elements</span></span>

<span data-ttu-id="29bee-108">Les sections suivantes décrivent les attributs, les éléments enfants et les éléments parents de l' `CustomEntry` élément.</span><span class="sxs-lookup"><span data-stu-id="29bee-108">The following sections describe attributes, child elements, and the parent elements of the `CustomEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="29bee-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="29bee-109">Attributes</span></span>

<span data-ttu-id="29bee-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="29bee-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="29bee-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="29bee-111">Child Elements</span></span>

|<span data-ttu-id="29bee-112">Élément</span><span class="sxs-lookup"><span data-stu-id="29bee-112">Element</span></span>|<span data-ttu-id="29bee-113">Description</span><span class="sxs-lookup"><span data-stu-id="29bee-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="29bee-114">EntrySelectedBy, élément pour CustomEntry pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="29bee-114">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="29bee-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="29bee-115">Optional element.</span></span><br /><br /> <span data-ttu-id="29bee-116">Définit les types .NET qui utilisent cette définition de contrôle ou la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="29bee-116">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="29bee-117">CustomItem, élément pour CustomEntry pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="29bee-117">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="29bee-118">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="29bee-118">Required element.</span></span><br /><br /> <span data-ttu-id="29bee-119">Définit le mode d’affichage des données par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="29bee-119">Defines how the control displays the data.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="29bee-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="29bee-120">Parent Elements</span></span>

|<span data-ttu-id="29bee-121">Élément</span><span class="sxs-lookup"><span data-stu-id="29bee-121">Element</span></span>|<span data-ttu-id="29bee-122">Description</span><span class="sxs-lookup"><span data-stu-id="29bee-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="29bee-123">CustomEntries, élément pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="29bee-123">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="29bee-124">Fournit les définitions pour le contrôle.</span><span class="sxs-lookup"><span data-stu-id="29bee-124">Provides the definitions for the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="29bee-125">Notes</span><span class="sxs-lookup"><span data-stu-id="29bee-125">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="29bee-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="29bee-126">See Also</span></span>

[<span data-ttu-id="29bee-127">CustomEntries, élément pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="29bee-127">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="29bee-128">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="29bee-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
