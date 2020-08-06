---
title: Élément CustomEntries pour CustomControl pour les contrôles pour View (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: a52bd2368044c34a0b73da331785d55597e30260
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783702"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-view-format"></a><span data-ttu-id="82a85-102">CustomEntries, élément pour CustomControl pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="82a85-102">CustomEntries Element for CustomControl for Controls for View (Format)</span></span>

<span data-ttu-id="82a85-103">Fournit les définitions pour le contrôle.</span><span class="sxs-lookup"><span data-stu-id="82a85-103">Provides the definitions for the control.</span></span> <span data-ttu-id="82a85-104">Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.</span><span class="sxs-lookup"><span data-stu-id="82a85-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="82a85-105">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) contrôle l’élément (format) contrôle élément pour les contrôles pour View (format) CustomControl, élément de Control pour les contrôles pour View (format) CustomEntries element pour CustomControl pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="82a85-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="82a85-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="82a85-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="82a85-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="82a85-107">Attributes and Elements</span></span>

<span data-ttu-id="82a85-108">Les sections suivantes décrivent les attributs, les éléments enfants et les éléments parents de l' `CustomEntries` élément.</span><span class="sxs-lookup"><span data-stu-id="82a85-108">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="82a85-109">Il n’existe pas de limite maximale pour le nombre d’éléments enfants qui peuvent être spécifiés.</span><span class="sxs-lookup"><span data-stu-id="82a85-109">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="82a85-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="82a85-110">Attributes</span></span>

<span data-ttu-id="82a85-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="82a85-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="82a85-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="82a85-112">Child Elements</span></span>

|<span data-ttu-id="82a85-113">Élément</span><span class="sxs-lookup"><span data-stu-id="82a85-113">Element</span></span>|<span data-ttu-id="82a85-114">Description</span><span class="sxs-lookup"><span data-stu-id="82a85-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="82a85-115">CustomEntry, élément pour CustomEntries pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="82a85-115">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="82a85-116">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="82a85-116">Required element.</span></span><br /><br /> <span data-ttu-id="82a85-117">Fournit une définition du contrôle.</span><span class="sxs-lookup"><span data-stu-id="82a85-117">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="82a85-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="82a85-118">Parent Elements</span></span>

|<span data-ttu-id="82a85-119">Élément</span><span class="sxs-lookup"><span data-stu-id="82a85-119">Element</span></span>|<span data-ttu-id="82a85-120">Description</span><span class="sxs-lookup"><span data-stu-id="82a85-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="82a85-121">CustomControl, élément pour Control pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="82a85-121">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="82a85-122">Définit le contrôle utilisé par la vue.</span><span class="sxs-lookup"><span data-stu-id="82a85-122">Defines the control used by the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="82a85-123">Notes</span><span class="sxs-lookup"><span data-stu-id="82a85-123">Remarks</span></span>

<span data-ttu-id="82a85-124">Dans la plupart des cas, un contrôle n’a qu’une seule définition, qui est spécifiée dans un `CustomEntry` élément unique.</span><span class="sxs-lookup"><span data-stu-id="82a85-124">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="82a85-125">Toutefois, il est possible de fournir plusieurs définitions si vous souhaitez utiliser le même contrôle pour afficher différents objets .NET.</span><span class="sxs-lookup"><span data-stu-id="82a85-125">However, it is possible to provide multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="82a85-126">Dans ce cas, vous pouvez définir un `CustomEntry` élément pour chaque objet ou ensemble d’objets.</span><span class="sxs-lookup"><span data-stu-id="82a85-126">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="82a85-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="82a85-127">See Also</span></span>

[<span data-ttu-id="82a85-128">CustomEntry, élément pour CustomEntries pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="82a85-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="82a85-129">CustomControl, élément pour Control pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="82a85-129">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="82a85-130">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="82a85-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
