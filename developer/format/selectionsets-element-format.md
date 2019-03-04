---
title: Élément SelectionSets (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebbac73a-1c99-4388-9f47-703cd024dc6d
caps.latest.revision: 18
ms.openlocfilehash: a9356635d60d5f8c5d4dec4ec8b7d0aea2b037dd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853565"
---
# <a name="selectionsets-element-format"></a><span data-ttu-id="38220-102">SelectionSets, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="38220-102">SelectionSets Element (Format)</span></span>

<span data-ttu-id="38220-103">Définit les jeux d’objets .NET qui peuvent être utilisées par toutes les vues du fichier de mise en forme courants.</span><span class="sxs-lookup"><span data-stu-id="38220-103">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span> <span data-ttu-id="38220-104">Les vues et les contrôles du fichier de mise en forme peuvent faire référence à l’ensemble complet des objets en utilisant uniquement le nom de l’ensemble de la sélection.</span><span class="sxs-lookup"><span data-stu-id="38220-104">The views and controls of the formatting file can reference the complete set of objects by using only the name of the selection set.</span></span>

<span data-ttu-id="38220-105">Format d’élément de SelectionSets élément de configuration</span><span class="sxs-lookup"><span data-stu-id="38220-105">Configuration Element SelectionSets Element Format</span></span>

## <a name="syntax"></a><span data-ttu-id="38220-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38220-106">Syntax</span></span>

```xml
<SelectionSets>
  <SelectionSet>...</SelectionSet>
</SelectionSets>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="38220-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="38220-107">Attributes and Elements</span></span>

<span data-ttu-id="38220-108">Les sections suivantes décrivent les attributs, éléments enfants et élément parent de la `SelectionSets` élément.</span><span class="sxs-lookup"><span data-stu-id="38220-108">The following sections describe the attributes, child elements, and parent element of the `SelectionSets` element.</span></span> <span data-ttu-id="38220-109">Chaque élément enfant définit un ensemble d’objets qui peuvent être référencés par le nom de l’ensemble.</span><span class="sxs-lookup"><span data-stu-id="38220-109">Each child element defines a set of objects that can be referenced by the name of the set.</span></span> <span data-ttu-id="38220-110">L’ordre des éléments enfants n’est pas significatif.</span><span class="sxs-lookup"><span data-stu-id="38220-110">The order of the child elements is not significant.</span></span>

### <a name="attributes"></a><span data-ttu-id="38220-111">Attributes</span><span class="sxs-lookup"><span data-stu-id="38220-111">Attributes</span></span>

<span data-ttu-id="38220-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="38220-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="38220-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="38220-113">Child Elements</span></span>

|<span data-ttu-id="38220-114">Élément</span><span class="sxs-lookup"><span data-stu-id="38220-114">Element</span></span>|<span data-ttu-id="38220-115">Description</span><span class="sxs-lookup"><span data-stu-id="38220-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="38220-116">Élément SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="38220-116">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="38220-117">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="38220-117">Required element.</span></span><br /><br /> <span data-ttu-id="38220-118">Définit un ensemble unique d’objets .NET qui peuvent être référencés par le nom de l’ensemble.</span><span class="sxs-lookup"><span data-stu-id="38220-118">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="38220-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="38220-119">Parent Elements</span></span>

|<span data-ttu-id="38220-120">Élément</span><span class="sxs-lookup"><span data-stu-id="38220-120">Element</span></span>|<span data-ttu-id="38220-121">Description</span><span class="sxs-lookup"><span data-stu-id="38220-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="38220-122">Élément de configuration</span><span class="sxs-lookup"><span data-stu-id="38220-122">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="38220-123">Représente l’élément de niveau supérieur d’un fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="38220-123">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="38220-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="38220-124">Remarks</span></span>

<span data-ttu-id="38220-125">Vous pouvez utiliser des jeux de sélection lorsque vous avez un ensemble d’objets connexes que vous souhaitez faire référence à l’aide d’un nom unique, comme un ensemble d’objets qui sont liés par héritage.</span><span class="sxs-lookup"><span data-stu-id="38220-125">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="38220-126">Lorsque vous définissez vos vues, vous pouvez spécifier le jeu d’objets en utilisant le nom de la sélection définie au lieu de répertorier tous les objets au sein de chaque vue.</span><span class="sxs-lookup"><span data-stu-id="38220-126">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="38220-127">Ensembles communs de sélection sont spécifiés par leur nom lorsque vous définissez les vues du fichier de mise en forme ou les définitions des vues.</span><span class="sxs-lookup"><span data-stu-id="38220-127">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="38220-128">Dans ce cas, le `SelectionSetName` élément enfant de le `ViewSelectedBy` et `EntrySelectedBy` éléments spécifie le jeu à utiliser.</span><span class="sxs-lookup"><span data-stu-id="38220-128">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="38220-129">Pour plus d’informations sur les jeux de sélection, consultez [définition définit des objets](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="38220-129">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="38220-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="38220-130">See Also</span></span>

[<span data-ttu-id="38220-131">Élément de configuration</span><span class="sxs-lookup"><span data-stu-id="38220-131">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="38220-132">Définition de jeux de sélection</span><span class="sxs-lookup"><span data-stu-id="38220-132">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="38220-133">Élément SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="38220-133">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="38220-134">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="38220-134">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
