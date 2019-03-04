---
title: Élément CustomEntries pour CustomControl pour les contrôles de Configuration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 80fc4de2-208f-4506-9a6a-c2675bb83be4
caps.latest.revision: 11
ms.openlocfilehash: abef6c91500f665c2366f221496d4cfd6444f5c9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856305"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="d0f02-102">CustomEntries, élément pour CustomControl pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="d0f02-102">CustomEntries Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="d0f02-103">Fournit les définitions d’un contrôle courant.</span><span class="sxs-lookup"><span data-stu-id="d0f02-103">Provides the definitions of a common control.</span></span> <span data-ttu-id="d0f02-104">Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="d0f02-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="d0f02-105">Élément de contrôles (Format) d’élément de configuration de l’élément de contrôle de Configuration (Format) pour les contrôles d’élément de CustomControl Configuration (Format) pour le contrôle de l’élément de Configuration (Format) de CustomEntries pour CustomControl pour la Configuration ( Format)</span><span class="sxs-lookup"><span data-stu-id="d0f02-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d0f02-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d0f02-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="d0f02-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="d0f02-107">Attributes and Elements</span></span>

<span data-ttu-id="d0f02-108">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `CustomEntries` élément.</span><span class="sxs-lookup"><span data-stu-id="d0f02-108">The following sections describe attributes, child elements, and the parent element of the `CustomEntries` element.</span></span> <span data-ttu-id="d0f02-109">Vous devez spécifier un ou plusieurs éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="d0f02-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="d0f02-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="d0f02-110">Attributes</span></span>

<span data-ttu-id="d0f02-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="d0f02-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d0f02-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d0f02-112">Child Elements</span></span>

|<span data-ttu-id="d0f02-113">Élément</span><span class="sxs-lookup"><span data-stu-id="d0f02-113">Element</span></span>|<span data-ttu-id="d0f02-114">Description</span><span class="sxs-lookup"><span data-stu-id="d0f02-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d0f02-115">Élément CustomEntry pour CustomControl pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="d0f02-115">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="d0f02-116">Fournit une définition du contrôle commun.</span><span class="sxs-lookup"><span data-stu-id="d0f02-116">Provides a definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d0f02-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d0f02-117">Parent Elements</span></span>

|<span data-ttu-id="d0f02-118">Élément</span><span class="sxs-lookup"><span data-stu-id="d0f02-118">Element</span></span>|<span data-ttu-id="d0f02-119">Description</span><span class="sxs-lookup"><span data-stu-id="d0f02-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d0f02-120">Élément CustomControl pour le contrôle de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="d0f02-120">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="d0f02-121">Définit un contrôle commun.</span><span class="sxs-lookup"><span data-stu-id="d0f02-121">Defines a common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d0f02-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="d0f02-122">Remarks</span></span>

<span data-ttu-id="d0f02-123">Dans la plupart des cas, un contrôle n'a qu’une seule définition, ce qui est définie dans un seul `CustomEntry` élément.</span><span class="sxs-lookup"><span data-stu-id="d0f02-123">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="d0f02-124">Toutefois, il est possible d’avoir plusieurs définitions si vous souhaitez utiliser le même contrôle pour afficher les différents objets .NET.</span><span class="sxs-lookup"><span data-stu-id="d0f02-124">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="d0f02-125">Dans ce cas, vous pouvez définir un `CustomEntry` élément pour chaque objet ou un ensemble d’objets.</span><span class="sxs-lookup"><span data-stu-id="d0f02-125">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="d0f02-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d0f02-126">See Also</span></span>

[<span data-ttu-id="d0f02-127">Élément CustomControl pour le contrôle de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="d0f02-127">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="d0f02-128">Élément CustomEntry pour CustomControl pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="d0f02-128">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="d0f02-129">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="d0f02-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
