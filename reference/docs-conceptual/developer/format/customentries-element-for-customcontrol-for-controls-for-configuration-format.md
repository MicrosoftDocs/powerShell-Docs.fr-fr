---
ms.date: 09/13/2016
ms.topic: reference
title: CustomEntries, élément pour CustomControl pour Controls pour Configuration (Format)
description: CustomEntries, élément pour CustomControl pour Controls pour Configuration (Format)
ms.openlocfilehash: 86c2b517d0d7075a355a3190a14e25d9dd4fe374
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655398"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="54923-103">CustomEntries, élément pour CustomControl pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="54923-103">CustomEntries Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="54923-104">Fournit les définitions d’un contrôle commun.</span><span class="sxs-lookup"><span data-stu-id="54923-104">Provides the definitions of a common control.</span></span> <span data-ttu-id="54923-105">Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="54923-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="54923-106">Élément de configuration (format) contrôle l’élément de configuration (format) élément de contrôle pour les contrôles de configuration (format) CustomControl élément de contrôle pour la configuration (format) élément CustomEntries pour CustomControl pour la configuration (format)</span><span class="sxs-lookup"><span data-stu-id="54923-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="54923-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="54923-107">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="54923-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="54923-108">Attributes and Elements</span></span>

<span data-ttu-id="54923-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `CustomEntries` élément.</span><span class="sxs-lookup"><span data-stu-id="54923-109">The following sections describe attributes, child elements, and the parent element of the `CustomEntries` element.</span></span> <span data-ttu-id="54923-110">Vous devez spécifier un ou plusieurs éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="54923-110">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="54923-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="54923-111">Attributes</span></span>

<span data-ttu-id="54923-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="54923-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="54923-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="54923-113">Child Elements</span></span>

|<span data-ttu-id="54923-114">Élément</span><span class="sxs-lookup"><span data-stu-id="54923-114">Element</span></span>|<span data-ttu-id="54923-115">Description</span><span class="sxs-lookup"><span data-stu-id="54923-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="54923-116">CustomEntry, élément pour CustomControl pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="54923-116">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="54923-117">Fournit une définition du contrôle commun.</span><span class="sxs-lookup"><span data-stu-id="54923-117">Provides a definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="54923-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="54923-118">Parent Elements</span></span>

|<span data-ttu-id="54923-119">Élément</span><span class="sxs-lookup"><span data-stu-id="54923-119">Element</span></span>|<span data-ttu-id="54923-120">Description</span><span class="sxs-lookup"><span data-stu-id="54923-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="54923-121">CustomControl, élément de Control pour la configuration (format)</span><span class="sxs-lookup"><span data-stu-id="54923-121">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="54923-122">Définit un contrôle commun.</span><span class="sxs-lookup"><span data-stu-id="54923-122">Defines a common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="54923-123">Notes</span><span class="sxs-lookup"><span data-stu-id="54923-123">Remarks</span></span>

<span data-ttu-id="54923-124">Dans la plupart des cas, un contrôle n’a qu’une seule définition, qui est définie dans un `CustomEntry` élément unique.</span><span class="sxs-lookup"><span data-stu-id="54923-124">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="54923-125">Toutefois, il est possible d’avoir plusieurs définitions si vous souhaitez utiliser le même contrôle pour afficher différents objets .NET.</span><span class="sxs-lookup"><span data-stu-id="54923-125">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="54923-126">Dans ce cas, vous pouvez définir un `CustomEntry` élément pour chaque objet ou ensemble d’objets.</span><span class="sxs-lookup"><span data-stu-id="54923-126">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="54923-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="54923-127">See Also</span></span>

[<span data-ttu-id="54923-128">CustomControl, élément de Control pour la configuration (format)</span><span class="sxs-lookup"><span data-stu-id="54923-128">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="54923-129">CustomEntry, élément pour CustomControl pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="54923-129">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="54923-130">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="54923-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
