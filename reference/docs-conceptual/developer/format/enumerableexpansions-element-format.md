---
ms.date: 09/13/2016
ms.topic: reference
title: EnumerableExpansions, élément (Format)
description: EnumerableExpansions, élément (Format)
ms.openlocfilehash: 789599e6ff368b4685c7937d5b6eb38618752f9e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660184"
---
# <a name="enumerableexpansions-element-format"></a><span data-ttu-id="53427-103">EnumerableExpansions, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="53427-103">EnumerableExpansions Element (Format)</span></span>

<span data-ttu-id="53427-104">Définit la façon dont les objets de collection .NET sont développés lorsqu’ils sont affichés dans une vue.</span><span class="sxs-lookup"><span data-stu-id="53427-104">Defines how .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="53427-105">Élément de configuration (format) DefaultSettings, élément (format) EnumerableExpansions, élément (format)</span><span class="sxs-lookup"><span data-stu-id="53427-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="53427-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="53427-106">Syntax</span></span>

```xml
<EnumerableExpansions>
  <EnumerableExpansion>...</EnumerableExpansion>
</EnumerableExpansions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="53427-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="53427-107">Attributes and Elements</span></span>

<span data-ttu-id="53427-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `EnumerableExpansions` élément.</span><span class="sxs-lookup"><span data-stu-id="53427-108">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansions` element.</span></span> <span data-ttu-id="53427-109">Il n’existe aucune limite quant au nombre d’éléments enfants que vous pouvez utiliser.</span><span class="sxs-lookup"><span data-stu-id="53427-109">There is no limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="53427-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="53427-110">Attributes</span></span>

<span data-ttu-id="53427-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="53427-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="53427-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="53427-112">Child Elements</span></span>

|<span data-ttu-id="53427-113">Élément</span><span class="sxs-lookup"><span data-stu-id="53427-113">Element</span></span>|<span data-ttu-id="53427-114">Description</span><span class="sxs-lookup"><span data-stu-id="53427-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="53427-115">EnumerableExpansion, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="53427-115">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="53427-116">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="53427-116">Optional element.</span></span><br /><br /> <span data-ttu-id="53427-117">Définit les objets de collection .NET spécifiques qui sont développés lorsqu’ils sont affichés dans une vue.</span><span class="sxs-lookup"><span data-stu-id="53427-117">Defines the specific .NET collection objects that are expanded when they are displayed in a view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="53427-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="53427-118">Parent Elements</span></span>

|<span data-ttu-id="53427-119">Élément</span><span class="sxs-lookup"><span data-stu-id="53427-119">Element</span></span>|<span data-ttu-id="53427-120">Description</span><span class="sxs-lookup"><span data-stu-id="53427-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="53427-121">DefaultSettings, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="53427-121">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="53427-122">Définit des paramètres communs qui s’appliquent à toutes les vues du fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="53427-122">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="53427-123">Notes</span><span class="sxs-lookup"><span data-stu-id="53427-123">Remarks</span></span>

<span data-ttu-id="53427-124">Cet élément est utilisé pour définir le mode d’affichage des objets de collection et des objets de la collection.</span><span class="sxs-lookup"><span data-stu-id="53427-124">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="53427-125">Dans ce cas, un objet de collection fait référence à tout objet qui prend en charge l’interface  **System. Collections. ICollection** .</span><span class="sxs-lookup"><span data-stu-id="53427-125">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="53427-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="53427-126">See Also</span></span>

[<span data-ttu-id="53427-127">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="53427-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
