---
ms.date: 09/13/2016
ms.topic: reference
title: CustomEntry, élément pour CustomControl pour Controls pour Configuration (Format)
description: CustomEntry, élément pour CustomControl pour Controls pour Configuration (Format)
ms.openlocfilehash: 3967be86a1d6c12c7215ef19d50bac9fafd5ad6d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648286"
---
# <a name="customentry-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="0fa56-103">CustomEntry, élément pour CustomControl pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="0fa56-103">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="0fa56-104">Fournit une définition du contrôle commun.</span><span class="sxs-lookup"><span data-stu-id="0fa56-104">Provides a definition of the common control.</span></span> <span data-ttu-id="0fa56-105">Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="0fa56-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="0fa56-106">Élément de configuration (format) contrôle l’élément de configuration (format) élément de contrôle pour les contrôles de configuration (format) CustomControl élément de contrôle pour la configuration (format) élément CustomEntries pour CustomControl pour la configuration (format) élément CustomEntry pour CustomControl pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="0fa56-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0fa56-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0fa56-107">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="0fa56-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0fa56-108">Attributes and Elements</span></span>

<span data-ttu-id="0fa56-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `CustomEntry` élément.</span><span class="sxs-lookup"><span data-stu-id="0fa56-109">The following sections describe attributes, child elements, and the parent element of the `CustomEntry` element.</span></span> <span data-ttu-id="0fa56-110">Vous devez spécifier les éléments affichés par la définition.</span><span class="sxs-lookup"><span data-stu-id="0fa56-110">You must specify the items displayed by the definition.</span></span>

### <a name="attributes"></a><span data-ttu-id="0fa56-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="0fa56-111">Attributes</span></span>

<span data-ttu-id="0fa56-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="0fa56-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0fa56-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0fa56-113">Child Elements</span></span>

|<span data-ttu-id="0fa56-114">Élément</span><span class="sxs-lookup"><span data-stu-id="0fa56-114">Element</span></span>|<span data-ttu-id="0fa56-115">Description</span><span class="sxs-lookup"><span data-stu-id="0fa56-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0fa56-116">EntrySelectedBy, élément pour CustomEntry pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="0fa56-116">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="0fa56-117">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="0fa56-117">Optional element.</span></span><br /><br /> <span data-ttu-id="0fa56-118">Définit les types .NET qui utilisent la définition du contrôle commun ou la condition qui doit exister pour que ce contrôle soit utilisé.</span><span class="sxs-lookup"><span data-stu-id="0fa56-118">Defines the .NET types that use the definition of the common control or the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="0fa56-119">Élément CustomItem pour CustomEntry pour les contrôles de configuration</span><span class="sxs-lookup"><span data-stu-id="0fa56-119">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="0fa56-120">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="0fa56-120">Required element.</span></span><br /><br /> <span data-ttu-id="0fa56-121">Définit les données affichées par le contrôle et leur mode d’affichage.</span><span class="sxs-lookup"><span data-stu-id="0fa56-121">Defines what data is displayed by the control and how it is displayed.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0fa56-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0fa56-122">Parent Elements</span></span>

|<span data-ttu-id="0fa56-123">Élément</span><span class="sxs-lookup"><span data-stu-id="0fa56-123">Element</span></span>|<span data-ttu-id="0fa56-124">Description</span><span class="sxs-lookup"><span data-stu-id="0fa56-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0fa56-125">Élément CustomEntries pour CustomControl pour la configuration (format)</span><span class="sxs-lookup"><span data-stu-id="0fa56-125">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="0fa56-126">Fournit les définitions du contrôle commun.</span><span class="sxs-lookup"><span data-stu-id="0fa56-126">Provides the definitions of the common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0fa56-127">Notes</span><span class="sxs-lookup"><span data-stu-id="0fa56-127">Remarks</span></span>

<span data-ttu-id="0fa56-128">Dans la plupart des cas, une seule définition est requise pour chaque contrôle personnalisé commun, mais il est possible d’avoir plusieurs définitions si vous souhaitez utiliser le même contrôle pour afficher différents objets .NET.</span><span class="sxs-lookup"><span data-stu-id="0fa56-128">In most cases, only one definition is required for each common custom control, but it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="0fa56-129">Dans ce cas, vous pouvez fournir une définition distincte pour chaque objet ou ensemble d’objets.</span><span class="sxs-lookup"><span data-stu-id="0fa56-129">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="0fa56-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0fa56-130">See Also</span></span>

[<span data-ttu-id="0fa56-131">Élément CustomEntries pour CustomControl pour la configuration (format)</span><span class="sxs-lookup"><span data-stu-id="0fa56-131">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="0fa56-132">Élément CustomItem pour CustomEntry pour les contrôles de configuration</span><span class="sxs-lookup"><span data-stu-id="0fa56-132">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="0fa56-133">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="0fa56-133">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
