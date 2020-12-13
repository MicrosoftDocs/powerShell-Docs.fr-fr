---
ms.date: 09/13/2016
ms.topic: reference
title: ScriptBlock, élément pour GroupBy (Format)
description: ScriptBlock, élément pour GroupBy (Format)
ms.openlocfilehash: 117cbef93889046626741449886a1caaa39815cb
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665238"
---
# <a name="scriptblock-element-for-groupby-format"></a><span data-ttu-id="c509e-103">ScriptBlock, élément pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="c509e-103">ScriptBlock Element for GroupBy (Format)</span></span>

<span data-ttu-id="c509e-104">Spécifie le script qui démarre un nouveau groupe chaque fois que sa valeur change.</span><span class="sxs-lookup"><span data-stu-id="c509e-104">Specifies the script that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="c509e-105">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément d’affichage (format) ScriptBlock pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="c509e-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) ScriptBlock Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c509e-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c509e-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c509e-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c509e-107">Attributes and Elements</span></span>

<span data-ttu-id="c509e-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ScriptBlock` élément.</span><span class="sxs-lookup"><span data-stu-id="c509e-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c509e-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="c509e-109">Attributes</span></span>

<span data-ttu-id="c509e-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="c509e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c509e-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c509e-111">Child Elements</span></span>

<span data-ttu-id="c509e-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="c509e-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c509e-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c509e-113">Parent Elements</span></span>

|<span data-ttu-id="c509e-114">Élément</span><span class="sxs-lookup"><span data-stu-id="c509e-114">Element</span></span>|<span data-ttu-id="c509e-115">Description</span><span class="sxs-lookup"><span data-stu-id="c509e-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c509e-116">GroupBy, élément pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="c509e-116">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="c509e-117">Définit le mode d’affichage d’un groupe d’objets .NET.</span><span class="sxs-lookup"><span data-stu-id="c509e-117">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c509e-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="c509e-118">Text Value</span></span>

<span data-ttu-id="c509e-119">Spécifiez le script qui est évalué.</span><span class="sxs-lookup"><span data-stu-id="c509e-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="c509e-120">Notes</span><span class="sxs-lookup"><span data-stu-id="c509e-120">Remarks</span></span>

<span data-ttu-id="c509e-121">PowerShell démarre un nouveau groupe chaque fois que la valeur de ce script change.</span><span class="sxs-lookup"><span data-stu-id="c509e-121">PowerShell starts a new group whenever the value of this script changes.</span></span>

<span data-ttu-id="c509e-122">Lorsque cet élément est spécifié, vous ne pouvez pas spécifier l’élément [PropertyName](propertyname-element-for-groupby-format.md) pour démarrer un nouveau groupe.</span><span class="sxs-lookup"><span data-stu-id="c509e-122">When this element is specified, you cannot specify the [PropertyName](propertyname-element-for-groupby-format.md) element to start a new group.</span></span>

## <a name="see-also"></a><span data-ttu-id="c509e-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c509e-123">See Also</span></span>

[<span data-ttu-id="c509e-124">PropertyName, élément pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="c509e-124">PropertyName Element for GroupBy (Format)</span></span>](propertyname-element-for-groupby-format.md)

[<span data-ttu-id="c509e-125">GroupBy, élément pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="c509e-125">GroupBy Element for View (Format)</span></span>](groupby-element-for-view-format.md)

[<span data-ttu-id="c509e-126">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="c509e-126">Writing a PowerShell Formatting File</span></span>](writing-a-powershell-formatting-file.md)
