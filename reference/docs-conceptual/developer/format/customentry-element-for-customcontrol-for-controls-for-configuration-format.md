---
title: Élément CustomEntry pour CustomControl pour les contrôles de configuration (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 8b9d18bbb1abce8135f4c27418ad54a1736eb5a6
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785929"
---
# <a name="customentry-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="9b059-102">CustomEntry, élément pour CustomControl pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="9b059-102">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="9b059-103">Fournit une définition du contrôle commun.</span><span class="sxs-lookup"><span data-stu-id="9b059-103">Provides a definition of the common control.</span></span> <span data-ttu-id="9b059-104">Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="9b059-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="9b059-105">Élément de configuration (format) contrôle l’élément de configuration (format) élément de contrôle pour les contrôles de configuration (format) CustomControl élément de contrôle pour la configuration (format) élément CustomEntries pour CustomControl pour la configuration (format) élément CustomEntry pour CustomControl pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="9b059-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9b059-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9b059-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="9b059-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="9b059-107">Attributes and Elements</span></span>

<span data-ttu-id="9b059-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `CustomEntry` élément.</span><span class="sxs-lookup"><span data-stu-id="9b059-108">The following sections describe attributes, child elements, and the parent element of the `CustomEntry` element.</span></span> <span data-ttu-id="9b059-109">Vous devez spécifier les éléments affichés par la définition.</span><span class="sxs-lookup"><span data-stu-id="9b059-109">You must specify the items displayed by the definition.</span></span>

### <a name="attributes"></a><span data-ttu-id="9b059-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="9b059-110">Attributes</span></span>

<span data-ttu-id="9b059-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="9b059-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9b059-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9b059-112">Child Elements</span></span>

|<span data-ttu-id="9b059-113">Élément</span><span class="sxs-lookup"><span data-stu-id="9b059-113">Element</span></span>|<span data-ttu-id="9b059-114">Description</span><span class="sxs-lookup"><span data-stu-id="9b059-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9b059-115">EntrySelectedBy, élément pour CustomEntry pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="9b059-115">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="9b059-116">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="9b059-116">Optional element.</span></span><br /><br /> <span data-ttu-id="9b059-117">Définit les types .NET qui utilisent la définition du contrôle commun ou la condition qui doit exister pour que ce contrôle soit utilisé.</span><span class="sxs-lookup"><span data-stu-id="9b059-117">Defines the .NET types that use the definition of the common control or the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="9b059-118">Élément CustomItem pour CustomEntry pour les contrôles de configuration</span><span class="sxs-lookup"><span data-stu-id="9b059-118">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="9b059-119">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="9b059-119">Required element.</span></span><br /><br /> <span data-ttu-id="9b059-120">Définit les données affichées par le contrôle et leur mode d’affichage.</span><span class="sxs-lookup"><span data-stu-id="9b059-120">Defines what data is displayed by the control and how it is displayed.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9b059-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9b059-121">Parent Elements</span></span>

|<span data-ttu-id="9b059-122">Élément</span><span class="sxs-lookup"><span data-stu-id="9b059-122">Element</span></span>|<span data-ttu-id="9b059-123">Description</span><span class="sxs-lookup"><span data-stu-id="9b059-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9b059-124">Élément CustomEntries pour CustomControl pour la configuration (format)</span><span class="sxs-lookup"><span data-stu-id="9b059-124">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="9b059-125">Fournit les définitions du contrôle commun.</span><span class="sxs-lookup"><span data-stu-id="9b059-125">Provides the definitions of the common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9b059-126">Notes</span><span class="sxs-lookup"><span data-stu-id="9b059-126">Remarks</span></span>

<span data-ttu-id="9b059-127">Dans la plupart des cas, une seule définition est requise pour chaque contrôle personnalisé commun, mais il est possible d’avoir plusieurs définitions si vous souhaitez utiliser le même contrôle pour afficher différents objets .NET.</span><span class="sxs-lookup"><span data-stu-id="9b059-127">In most cases, only one definition is required for each common custom control, but it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="9b059-128">Dans ce cas, vous pouvez fournir une définition distincte pour chaque objet ou ensemble d’objets.</span><span class="sxs-lookup"><span data-stu-id="9b059-128">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="9b059-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9b059-129">See Also</span></span>

[<span data-ttu-id="9b059-130">Élément CustomEntries pour CustomControl pour la configuration (format)</span><span class="sxs-lookup"><span data-stu-id="9b059-130">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="9b059-131">Élément CustomItem pour CustomEntry pour les contrôles de configuration</span><span class="sxs-lookup"><span data-stu-id="9b059-131">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="9b059-132">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="9b059-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
