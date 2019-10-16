---
title: Élément SelectionSets (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebbac73a-1c99-4388-9f47-703cd024dc6d
caps.latest.revision: 18
ms.openlocfilehash: a9356635d60d5f8c5d4dec4ec8b7d0aea2b037dd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361868"
---
# <a name="selectionsets-element-format"></a><span data-ttu-id="577bc-102">SelectionSets, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="577bc-102">SelectionSets Element (Format)</span></span>

<span data-ttu-id="577bc-103">Définit les ensembles courants d’objets .NET qui peuvent être utilisés par toutes les vues du fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="577bc-103">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span> <span data-ttu-id="577bc-104">Les vues et les contrôles du fichier de mise en forme peuvent faire référence à l’ensemble complet d’objets en utilisant uniquement le nom du jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="577bc-104">The views and controls of the formatting file can reference the complete set of objects by using only the name of the selection set.</span></span>

<span data-ttu-id="577bc-105">Format d’élément SelectionSets de l’élément de configuration</span><span class="sxs-lookup"><span data-stu-id="577bc-105">Configuration Element SelectionSets Element Format</span></span>

## <a name="syntax"></a><span data-ttu-id="577bc-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="577bc-106">Syntax</span></span>

```xml
<SelectionSets>
  <SelectionSet>...</SelectionSet>
</SelectionSets>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="577bc-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="577bc-107">Attributes and Elements</span></span>

<span data-ttu-id="577bc-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `SelectionSets`.</span><span class="sxs-lookup"><span data-stu-id="577bc-108">The following sections describe the attributes, child elements, and parent element of the `SelectionSets` element.</span></span> <span data-ttu-id="577bc-109">Chaque élément enfant définit un ensemble d’objets qui peuvent être référencés par le nom de l’ensemble.</span><span class="sxs-lookup"><span data-stu-id="577bc-109">Each child element defines a set of objects that can be referenced by the name of the set.</span></span> <span data-ttu-id="577bc-110">L’ordre des éléments enfants n’est pas significatif.</span><span class="sxs-lookup"><span data-stu-id="577bc-110">The order of the child elements is not significant.</span></span>

### <a name="attributes"></a><span data-ttu-id="577bc-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="577bc-111">Attributes</span></span>

<span data-ttu-id="577bc-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="577bc-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="577bc-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="577bc-113">Child Elements</span></span>

|<span data-ttu-id="577bc-114">Élément</span><span class="sxs-lookup"><span data-stu-id="577bc-114">Element</span></span>|<span data-ttu-id="577bc-115">Description</span><span class="sxs-lookup"><span data-stu-id="577bc-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="577bc-116">Élément SelectionSet (format)</span><span class="sxs-lookup"><span data-stu-id="577bc-116">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="577bc-117">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="577bc-117">Required element.</span></span><br /><br /> <span data-ttu-id="577bc-118">Définit un ensemble unique d’objets .NET qui peuvent être référencés par le nom de l’ensemble.</span><span class="sxs-lookup"><span data-stu-id="577bc-118">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="577bc-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="577bc-119">Parent Elements</span></span>

|<span data-ttu-id="577bc-120">Élément</span><span class="sxs-lookup"><span data-stu-id="577bc-120">Element</span></span>|<span data-ttu-id="577bc-121">Description</span><span class="sxs-lookup"><span data-stu-id="577bc-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="577bc-122">Élément de configuration</span><span class="sxs-lookup"><span data-stu-id="577bc-122">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="577bc-123">Représente l’élément de niveau supérieur d’un fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="577bc-123">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="577bc-124">Remarks</span><span class="sxs-lookup"><span data-stu-id="577bc-124">Remarks</span></span>

<span data-ttu-id="577bc-125">Vous pouvez utiliser des jeux de sélection quand vous avez un ensemble d’objets connexes que vous souhaitez référencer à l’aide d’un nom unique, tel qu’un ensemble d’objets liés par héritage.</span><span class="sxs-lookup"><span data-stu-id="577bc-125">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="577bc-126">Lorsque vous définissez vos vues, vous pouvez spécifier le jeu d’objets en utilisant le nom du jeu de sélection au lieu de répertorier tous les objets dans chaque vue.</span><span class="sxs-lookup"><span data-stu-id="577bc-126">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="577bc-127">Les jeux de sélection communs sont spécifiés par leur nom lors de la définition des vues du fichier de mise en forme ou des définitions des vues.</span><span class="sxs-lookup"><span data-stu-id="577bc-127">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="577bc-128">Dans ce cas, l’élément enfant `SelectionSetName` des éléments `ViewSelectedBy` et `EntrySelectedBy` spécifie le jeu à utiliser.</span><span class="sxs-lookup"><span data-stu-id="577bc-128">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="577bc-129">Pour plus d’informations sur les jeux de sélection, consultez [définition de jeux d’objets](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="577bc-129">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="577bc-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="577bc-130">See Also</span></span>

[<span data-ttu-id="577bc-131">Élément de configuration</span><span class="sxs-lookup"><span data-stu-id="577bc-131">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="577bc-132">Définition des jeux de sélection</span><span class="sxs-lookup"><span data-stu-id="577bc-132">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="577bc-133">Élément SelectionSet (format)</span><span class="sxs-lookup"><span data-stu-id="577bc-133">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="577bc-134">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="577bc-134">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
