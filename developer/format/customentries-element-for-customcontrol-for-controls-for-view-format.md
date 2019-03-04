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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861805"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-view-format"></a><span data-ttu-id="0f98a-102">CustomEntries, élément pour CustomControl pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="0f98a-102">CustomEntries Element for CustomControl for Controls for View (Format)</span></span>

<span data-ttu-id="0f98a-103">Fournit les définitions pour le contrôle.</span><span class="sxs-lookup"><span data-stu-id="0f98a-103">Provides the definitions for the control.</span></span> <span data-ttu-id="0f98a-104">Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.</span><span class="sxs-lookup"><span data-stu-id="0f98a-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="0f98a-105">Élément (Format) élément ViewDefinitions (Format) vue élément (Format) contrôles élément (Format) contrôle élément de configuration pour les contrôles d’élément de CustomControl vue (Format) pour le contrôle pour les contrôles d’élément de CustomEntries vue (Format) pour CustomControl pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="0f98a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0f98a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0f98a-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0f98a-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="0f98a-107">Attributes and Elements</span></span>

<span data-ttu-id="0f98a-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents de la `CustomEntries` élément.</span><span class="sxs-lookup"><span data-stu-id="0f98a-108">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="0f98a-109">Il n’existe aucune limite maximale pour le nombre d’éléments enfants qui peuvent être spécifiées.</span><span class="sxs-lookup"><span data-stu-id="0f98a-109">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="0f98a-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="0f98a-110">Attributes</span></span>

<span data-ttu-id="0f98a-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="0f98a-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0f98a-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0f98a-112">Child Elements</span></span>

|<span data-ttu-id="0f98a-113">Élément</span><span class="sxs-lookup"><span data-stu-id="0f98a-113">Element</span></span>|<span data-ttu-id="0f98a-114">Description</span><span class="sxs-lookup"><span data-stu-id="0f98a-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0f98a-115">Élément CustomEntry pour CustomEntries pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="0f98a-115">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="0f98a-116">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="0f98a-116">Required element.</span></span><br /><br /> <span data-ttu-id="0f98a-117">Fournit une définition du contrôle.</span><span class="sxs-lookup"><span data-stu-id="0f98a-117">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0f98a-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0f98a-118">Parent Elements</span></span>

|<span data-ttu-id="0f98a-119">Élément</span><span class="sxs-lookup"><span data-stu-id="0f98a-119">Element</span></span>|<span data-ttu-id="0f98a-120">Description</span><span class="sxs-lookup"><span data-stu-id="0f98a-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0f98a-121">Élément CustomControl pour le contrôle pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="0f98a-121">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="0f98a-122">Définit le contrôle utilisé par la vue.</span><span class="sxs-lookup"><span data-stu-id="0f98a-122">Defines the control used by the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0f98a-123">Remarques</span><span class="sxs-lookup"><span data-stu-id="0f98a-123">Remarks</span></span>

<span data-ttu-id="0f98a-124">Dans la plupart des cas, un contrôle n'a qu’une seule définition, ce qui est spécifiée dans un seul `CustomEntry` élément.</span><span class="sxs-lookup"><span data-stu-id="0f98a-124">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="0f98a-125">Toutefois, il est possible de fournir plusieurs définitions si vous souhaitez utiliser le même contrôle pour afficher les différents objets .NET.</span><span class="sxs-lookup"><span data-stu-id="0f98a-125">However, it is possible to provide multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="0f98a-126">Dans ce cas, vous pouvez définir un `CustomEntry` élément pour chaque objet ou un ensemble d’objets.</span><span class="sxs-lookup"><span data-stu-id="0f98a-126">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="0f98a-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0f98a-127">See Also</span></span>

[<span data-ttu-id="0f98a-128">Élément CustomEntry pour CustomEntries pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="0f98a-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="0f98a-129">Élément CustomControl pour le contrôle pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="0f98a-129">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="0f98a-130">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="0f98a-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
