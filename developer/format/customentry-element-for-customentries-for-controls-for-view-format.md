---
title: Élément CustomEntry pour CustomEntries pour les contrôles de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6739205-2bc9-4507-b2af-d19d548c2057
caps.latest.revision: 6
ms.openlocfilehash: b92b99d88992cf13dbf7bfbe88aad603615f3138
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066483"
---
# <a name="customentry-element-for-customentries-for-controls-for-view-format"></a><span data-ttu-id="af8a3-102">CustomEntry, élément pour CustomEntries pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="af8a3-102">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>

<span data-ttu-id="af8a3-103">Fournit une définition du contrôle.</span><span class="sxs-lookup"><span data-stu-id="af8a3-103">Provides a definition of the control.</span></span> <span data-ttu-id="af8a3-104">Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.</span><span class="sxs-lookup"><span data-stu-id="af8a3-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="af8a3-105">Élément (Format) élément ViewDefinitions (Format) vue élément (Format) contrôles élément (Format) contrôle élément de configuration pour les contrôles d’élément de CustomControl vue (Format) pour le contrôle pour les contrôles d’élément de CustomEntries vue (Format) pour CustomControl pour l’élément d’affichage (Format) de CustomEntry pour CustomEntries pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="af8a3-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="af8a3-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af8a3-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="af8a3-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="af8a3-107">Attributes and Elements</span></span>

<span data-ttu-id="af8a3-108">Les sections suivantes décrivent les attributs, éléments enfants et les éléments parents de la `CustomEntry` élément.</span><span class="sxs-lookup"><span data-stu-id="af8a3-108">The following sections describe attributes, child elements, and the parent elements of the `CustomEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="af8a3-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="af8a3-109">Attributes</span></span>

<span data-ttu-id="af8a3-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="af8a3-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="af8a3-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="af8a3-111">Child Elements</span></span>

|<span data-ttu-id="af8a3-112">Élément</span><span class="sxs-lookup"><span data-stu-id="af8a3-112">Element</span></span>|<span data-ttu-id="af8a3-113">Description</span><span class="sxs-lookup"><span data-stu-id="af8a3-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="af8a3-114">Élément EntrySelectedBy pour CustomEntry pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="af8a3-114">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="af8a3-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="af8a3-115">Optional element.</span></span><br /><br /> <span data-ttu-id="af8a3-116">Définit les types .NET qui utilisent cette définition de contrôle ou la condition qui doit exister pour cette définition à utiliser.</span><span class="sxs-lookup"><span data-stu-id="af8a3-116">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="af8a3-117">Élément CustomItem pour CustomEntry pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="af8a3-117">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="af8a3-118">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="af8a3-118">Required element.</span></span><br /><br /> <span data-ttu-id="af8a3-119">Définit comment le contrôle affiche les données.</span><span class="sxs-lookup"><span data-stu-id="af8a3-119">Defines how the control displays the data.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="af8a3-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="af8a3-120">Parent Elements</span></span>

|<span data-ttu-id="af8a3-121">Élément</span><span class="sxs-lookup"><span data-stu-id="af8a3-121">Element</span></span>|<span data-ttu-id="af8a3-122">Description</span><span class="sxs-lookup"><span data-stu-id="af8a3-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="af8a3-123">Élément CustomEntries pour CustomControl de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="af8a3-123">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="af8a3-124">Fournit les définitions pour le contrôle.</span><span class="sxs-lookup"><span data-stu-id="af8a3-124">Provides the definitions for the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="af8a3-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="af8a3-125">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="af8a3-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="af8a3-126">See Also</span></span>

[<span data-ttu-id="af8a3-127">Élément CustomEntries pour CustomControl de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="af8a3-127">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="af8a3-128">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="af8a3-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
