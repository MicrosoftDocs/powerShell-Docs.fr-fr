---
title: Élément CustomEntries pour CustomControl pour les contrôles de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3485958a-ba87-4932-907c-a8f140c4abdb
caps.latest.revision: 8
ms.openlocfilehash: 4856aee930285781a101868bd6cb67824585bce1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066578"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-view-format"></a><span data-ttu-id="c66d0-102">CustomEntries, élément pour CustomControl pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="c66d0-102">CustomEntries Element for CustomControl for Controls for View (Format)</span></span>

<span data-ttu-id="c66d0-103">Fournit les définitions pour le contrôle.</span><span class="sxs-lookup"><span data-stu-id="c66d0-103">Provides the definitions for the control.</span></span> <span data-ttu-id="c66d0-104">Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.</span><span class="sxs-lookup"><span data-stu-id="c66d0-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="c66d0-105">Élément (Format) élément ViewDefinitions (Format) vue élément (Format) contrôles élément (Format) contrôle élément de configuration pour les contrôles d’élément de CustomControl vue (Format) pour le contrôle pour les contrôles d’élément de CustomEntries vue (Format) pour CustomControl pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="c66d0-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c66d0-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c66d0-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c66d0-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="c66d0-107">Attributes and Elements</span></span>

<span data-ttu-id="c66d0-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents de la `CustomEntries` élément.</span><span class="sxs-lookup"><span data-stu-id="c66d0-108">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="c66d0-109">Il n’existe aucune limite maximale pour le nombre d’éléments enfants qui peuvent être spécifiées.</span><span class="sxs-lookup"><span data-stu-id="c66d0-109">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="c66d0-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="c66d0-110">Attributes</span></span>

<span data-ttu-id="c66d0-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="c66d0-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c66d0-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c66d0-112">Child Elements</span></span>

|<span data-ttu-id="c66d0-113">Élément</span><span class="sxs-lookup"><span data-stu-id="c66d0-113">Element</span></span>|<span data-ttu-id="c66d0-114">Description</span><span class="sxs-lookup"><span data-stu-id="c66d0-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c66d0-115">Élément CustomEntry pour CustomEntries pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="c66d0-115">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="c66d0-116">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="c66d0-116">Required element.</span></span><br /><br /> <span data-ttu-id="c66d0-117">Fournit une définition du contrôle.</span><span class="sxs-lookup"><span data-stu-id="c66d0-117">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c66d0-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c66d0-118">Parent Elements</span></span>

|<span data-ttu-id="c66d0-119">Élément</span><span class="sxs-lookup"><span data-stu-id="c66d0-119">Element</span></span>|<span data-ttu-id="c66d0-120">Description</span><span class="sxs-lookup"><span data-stu-id="c66d0-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c66d0-121">Élément CustomControl pour le contrôle pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="c66d0-121">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="c66d0-122">Définit le contrôle utilisé par la vue.</span><span class="sxs-lookup"><span data-stu-id="c66d0-122">Defines the control used by the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c66d0-123">Remarques</span><span class="sxs-lookup"><span data-stu-id="c66d0-123">Remarks</span></span>

<span data-ttu-id="c66d0-124">Dans la plupart des cas, un contrôle n'a qu’une seule définition, ce qui est spécifiée dans un seul `CustomEntry` élément.</span><span class="sxs-lookup"><span data-stu-id="c66d0-124">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="c66d0-125">Toutefois, il est possible de fournir plusieurs définitions si vous souhaitez utiliser le même contrôle pour afficher les différents objets .NET.</span><span class="sxs-lookup"><span data-stu-id="c66d0-125">However, it is possible to provide multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="c66d0-126">Dans ce cas, vous pouvez définir un `CustomEntry` élément pour chaque objet ou un ensemble d’objets.</span><span class="sxs-lookup"><span data-stu-id="c66d0-126">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="c66d0-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c66d0-127">See Also</span></span>

[<span data-ttu-id="c66d0-128">Élément CustomEntry pour CustomEntries pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="c66d0-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="c66d0-129">Élément CustomControl pour le contrôle pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="c66d0-129">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="c66d0-130">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="c66d0-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
