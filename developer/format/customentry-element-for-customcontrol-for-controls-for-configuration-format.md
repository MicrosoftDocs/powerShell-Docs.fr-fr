---
title: Élément CustomEntry pour CustomControl pour les contrôles de Configuration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9dfba86f-29b2-473c-9e98-9d679176acce
caps.latest.revision: 11
ms.openlocfilehash: 497485a388d1cdc834ecc1d1079b0714a7d7f9db
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859805"
---
# <a name="customentry-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="9ee88-102">CustomEntry, élément pour CustomControl pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="9ee88-102">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="9ee88-103">Fournit une définition du contrôle commun.</span><span class="sxs-lookup"><span data-stu-id="9ee88-103">Provides a definition of the common control.</span></span> <span data-ttu-id="9ee88-104">Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="9ee88-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="9ee88-105">Élément de contrôles (Format) d’élément de configuration de l’élément de contrôle de Configuration (Format) pour les contrôles d’élément de CustomControl Configuration (Format) pour le contrôle de l’élément de Configuration (Format) de CustomEntries pour CustomControl pour la Configuration ( Élément CustomEntry de format) pour CustomControl pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="9ee88-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9ee88-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ee88-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="9ee88-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="9ee88-107">Attributes and Elements</span></span>

<span data-ttu-id="9ee88-108">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `CustomEntry` élément.</span><span class="sxs-lookup"><span data-stu-id="9ee88-108">The following sections describe attributes, child elements, and the parent element of the `CustomEntry` element.</span></span> <span data-ttu-id="9ee88-109">Vous devez spécifier les éléments affichés par la définition.</span><span class="sxs-lookup"><span data-stu-id="9ee88-109">You must specify the items displayed by the definition.</span></span>

### <a name="attributes"></a><span data-ttu-id="9ee88-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="9ee88-110">Attributes</span></span>

<span data-ttu-id="9ee88-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="9ee88-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9ee88-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9ee88-112">Child Elements</span></span>

|<span data-ttu-id="9ee88-113">Élément</span><span class="sxs-lookup"><span data-stu-id="9ee88-113">Element</span></span>|<span data-ttu-id="9ee88-114">Description</span><span class="sxs-lookup"><span data-stu-id="9ee88-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9ee88-115">Élément EntrySelectedBy pour CustomEntry pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="9ee88-115">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="9ee88-116">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="9ee88-116">Optional element.</span></span><br /><br /> <span data-ttu-id="9ee88-117">Définit les types .NET qui utilisent la définition du contrôle commun ou la condition qui doit exister pour ce contrôle à utiliser.</span><span class="sxs-lookup"><span data-stu-id="9ee88-117">Defines the .NET types that use the definition of the common control or the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="9ee88-118">Élément CustomItem pour CustomEntry pour les contrôles de Configuration</span><span class="sxs-lookup"><span data-stu-id="9ee88-118">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="9ee88-119">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="9ee88-119">Required element.</span></span><br /><br /> <span data-ttu-id="9ee88-120">Définit les données affichées par le contrôle et comment il est affiché.</span><span class="sxs-lookup"><span data-stu-id="9ee88-120">Defines what data is displayed by the control and how it is displayed.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9ee88-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9ee88-121">Parent Elements</span></span>

|<span data-ttu-id="9ee88-122">Élément</span><span class="sxs-lookup"><span data-stu-id="9ee88-122">Element</span></span>|<span data-ttu-id="9ee88-123">Description</span><span class="sxs-lookup"><span data-stu-id="9ee88-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9ee88-124">Élément CustomEntries pour CustomControl pour la Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="9ee88-124">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="9ee88-125">Fournit les définitions du contrôle commun.</span><span class="sxs-lookup"><span data-stu-id="9ee88-125">Provides the definitions of the common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9ee88-126">Remarques</span><span class="sxs-lookup"><span data-stu-id="9ee88-126">Remarks</span></span>

<span data-ttu-id="9ee88-127">Dans la plupart des cas, qu’une seule définition est requise pour chaque contrôle personnalisé courants, mais il est possible d’avoir plusieurs définitions si vous souhaitez utiliser le même contrôle pour afficher les différents objets .NET.</span><span class="sxs-lookup"><span data-stu-id="9ee88-127">In most cases, only one definition is required for each common custom control, but it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="9ee88-128">Dans ce cas, vous pouvez fournir une définition séparée pour chaque objet ou un ensemble d’objets.</span><span class="sxs-lookup"><span data-stu-id="9ee88-128">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="9ee88-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9ee88-129">See Also</span></span>

[<span data-ttu-id="9ee88-130">Élément CustomEntries pour CustomControl pour la Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="9ee88-130">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="9ee88-131">Élément CustomItem pour CustomEntry pour les contrôles de Configuration</span><span class="sxs-lookup"><span data-stu-id="9ee88-131">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="9ee88-132">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="9ee88-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
